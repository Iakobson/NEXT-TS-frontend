# How to Think About Security in Next.js

## Choosing Your Data Handling Model

[React Server Components](https://nextjs.org/docs/app/building-your-application/rendering/server-components) стирають межу між сервером і клієнтом. 
Обробка даних має першорядне значення для розуміння того, де інформація обробляється та згодом стає доступною.

Перше, що нам потрібно зробити, це вибрати що саме підходить для нашого проекту.
+ **HTTP API** (рекомендовано для існуючих великих проектів/організацій)
+ **Data Access Layer** (рекомендовано для нових проектів)
+ **Component Level Data Access** (рекомендовано для прототипування та навчання)

Ми рекомендуємо вам дотримуватися одного підходу та не змішувати занадто багато. 

### HTTP APIs

Якщо у вас вже є великий проект або організація, то рекомендовано використовувати **HTTP APIs** для обробки даних. Це означає, що **Server Components** слід розглядати як небезпечні або ненадійні за замовчуванням, так само, як інші техніки обробки даних.

#### Обробка Server Components:

Server Components розглядаються як небезпечні за замовчуванням, і для них не передбачається внутрішня мережа чи зони довіри.\
Інженери можуть застосовувати концепцію **"Zero Trust"** - не довіряти нічому, навіть якщо код виконується в середовищі, якому можна довіряти.

#### Робота з API:

Замість використання внутрішніх з'єднань або зон довіри, **Server Components** взаємодіють із зовнішніми **API**-точками, такими як **REST** або **GraphQL**, використовуючи `fetch()`. Це дозволяє передавати куки для автентифікації.

#### Оновлення існуючого коду:

Якщо у вас вже є функції, які підключаються до бази даних (наприклад, `getStaticProps` чи `getServerSideProps`), рекомендовано перенести їх до **API**-точок, щоб у вас був єдиний спосіб обробки даних.

#### Безпека:

Важливо слідкувати за контролем доступу, оскільки **Server Components** тепер розглядаються як небезпечні. Не передбачається, що запити з внутрішньої мережі є безпечними.

#### Організаційні переваги:

Такий підхід дозволяє зберігати існуючі організаційні структури. Наприклад, команди **backend**, які спеціалізуються на безпеці, можуть продовжити використовувати свої практики безпеки.

#### Переваги Server Components:

При цьому ви все ще можите скористатися перевагами Server Components, які полягають в надсиланні менше коду на клієнт і можливості виконання даних з низькою затримкою.

### Data Access Layer

Коли ви створюєте новий веб-проект, добре мати особливий "рівень", який відповідає за роботу з даними. Він буде в середині вашого коду і відповідатиме за те, як саме ваша програма отримує та обробляє дані. Цей рівень допомагає уникнути помилок та полегшує роботу з даними, оскільки все зосереджено в одній "бібліотеці". Це може зробити командну роботу більш ефективною та покращити продуктивність.

Ви створюєте такий спеціальний "кодовий пакет" у вашому JavaScript-коді, який гарантує, що доступ до даних відбувається однаково та безпечно. Ваша програма буде використовувати цей пакет, щоб взаємодіяти з даними. Він буде перевіряти, чи користувач має дозвіл на перегляд певних даних перед їх поверненням. Принцип полягає в тому, що функції, які відповідають за відображення даних, мають доступ лише до тих даних, до яких у користувача є дозвіл.

Після цього вам просто слідувати стандартним правилам безпеки при створенні свого API.

```typescript
  // @data/auth.tsx
  import { cache } from 'react';
  import { cookies } from 'next/headers';
 
  /*
    Кешовані допоміжні методи полегшують отримання одного й того ж значення в багатьох місцях
    без ручного передавання його навколо. Це дисциплінує передачу його від Server Component
    до Server Component, що мінімізує ризик передачі його до Client Component.
 */
  export const getCurrentUser = cache(async () => {
    const token = cookies().get('AUTH_TOKEN');
    const decodedToken = await decryptAndValidate(token);
    /*
      Не включайте секретні токени або особисту інформацію як публічні поля.
      Використовуйте класи, щоб уникнути випадкового передавання цілого об'єкта клієнту.
    */
    return new User(decodedToken.id);
  });
```

```typescript
  // @data/user-dto.tsx
  import 'server-only';
  import { getCurrentUser } from './auth';
 
  function canSeeUsername(viewer: User) {
    // Public info for now, but can change
    return true;
  }
 
  function canSeePhoneNumber(viewer: User, team: string) {
    // Privacy rules
    return viewer.isAdmin || team === viewer.team;
  }
 
  export async function getProfileDTO(slug: string) {
    // Don't pass values, read back cached values, also solves context and easier to make it lazy
 
    // use a database API that supports safe templating of queries
    const [rows] = await sql`SELECT * FROM user WHERE slug = ${slug}`;
    const userData = rows[0];
 
    const currentUser = await getCurrentUser();
 
    // only return the data relevant for this query and not everything
    // <https://www.w3.org/2001/tag/doc/APIMinimization>
    return {
      username: canSeeUsername(currentUser) ? userData.username : null,
      phonenumber: canSeePhoneNumber(currentUser, userData.team)
        ? userData.phonenumber
        : null,
    };
  }
```

Ці методи повинні представляти об'єкти, які можна безпечно надсилати клієнту без будь-яких змін. Ми називаємо їх "об'єктами передачі даних" (DTO), щоб підкреслити, що вони готові для використання клієнтом.

На практиці ці об'єкти можуть використовуватися переважно тільки в Server Components. Це створює дві шари безпеки: один для доступу до даних та інший для інтерфейсу користувача. Такий підхід полегшує перевірку безпеки, оскільки менше коду потрібно перевіряти на можливі проблеми.

```typescript
  import {getProfile} from '../../data/user'
  export async function Page({ params: { slug } }) {
    /*
      Тепер ця сторінка може безпечно передавати цей профіль,
      знаючи, що він не повинен містити нічого конфіденційного.
    */
    const profile = await getProfile(slug);
    // решта коду...
  }
```


### Component Level Data Access














