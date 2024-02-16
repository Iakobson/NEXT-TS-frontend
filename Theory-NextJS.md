# 🤖 Theory Next.JS 🤖

🌐 **Next.JS** - це **фреймворк** для розробки веб-додатків за допомогою JavaScript/TypeScript та React.js (бібіліотека відмальовки веб-сторінок).
Він містить клієнтську та серверну частини. Він дозволяє створювати повноцінні веб-застосунки без додаткових залежностей.

🌐 Next.JS за замовчуванням працює на сервері.

💥 💥 💥 💥 💥
  + роутер із коробки;
  + СЕО - створення сторінки на сервері;
  + рендер в статику;
  + можливість виконання серверного коду;
  + оптимізація зображень та шрифтів;
  + передналаштований EsLint.

🧙 Створення проекту: 💨 ``npx create-next-app@latest project-name``.

🧞 Запуск програми: 💨 ``npm run dev``

- - -

## 🔥 Top libraries for NextJS project 🏆

https://dev.to/nevodavid/top-12-libraries-for-your-nextjs-project-1oob

### 🌐 [Auth.js](https://authjs.dev/)
_Authentication for the Web._
  * NextAuth.js Example App 
    + https://github.com/nextauthjs/next-auth-example
      - _open source authentication solution_
    + https://next-auth-example.vercel.app/
      - _Server Side & Client Side_
  * Tutorials and Explainers
    + https://next-auth.js.org/tutorials

#### 💨 Auth0 🔥
  * **Next.js SDK** for signing in with Auth0
    + https://github.com/auth0/nextjs-auth0
      - _library for implementing user authentication in Next.js applications_
  * Next.js Authentication By Example:
    + https://developer.auth0.com/resources/guides/web-app/nextjs/basic-authentication
      - Using App Router





- - -

## Version 13.4.2
_оновлено 16.05.2023_

#### Router
* всі маніпуляції зі шляхом виконуються на рівні теки
* файл сторінки має завжди називатися page.tsx
* підтримуються індивідуальні layout/loading/error
* можливі вкладені компоненти
  - _layout вкладаються один в одного_
  - _використання повноцінних підсторінок_

#### API

* файл роуту має завжди називатися route.ts
* Response став окремим статичним класом


### Серверні Компоненти

* таким є усі за замовчуванням
* можемо використовувати асинхронні функції
* однак не працює CSS in JS


### Клієнтські Компоненти

* директива ``"use client"
  - _автоматично усі імпортовані модулі_
 


### структура робочих файлів проекту

```go
📁project-name/
│
├─ package.json
├─ tsconfig.json
├─ next.config
├─ next-env.d
│
├─ 📁app/
│  │
│  ├─ globals.css
│  ├─ layout.tsx
│  ├─ page.module.css
│  ├─ page.tsx
│  │
│  ├─ 📁some/
│  │  ├─ layout.tsx
│  │  │
│  │  ├─ 📁lesson/
│  │  │  ├─ page.tsx
│  │  │  
│  │  ├─ 📁another/
│  │  │  ├─ page.tsx
│  │
│  │
│  ├─ 📁api/
│
│
├─ 📁public/

```

- - -

## Version 13.3.3
_оновлено 01.05.2023_

### структура робочих файлів проекту

```go
📁project-name/
│
├─ package.json
├─ tsconfig.json
├─ next.config
├─ next-env.d
│
├─ 📁src/
│  │
│  ├─ 📁pages/
│  │  ├─ _app.ts // службова обгортка для кожної сторінки
│  │  ├─ _document.ts // дозволяє модифікувати структуру доумента
│  │  ├─ index.ts // відповідає за першу сторінку
│  │  ├─ about.tsx // певна сторінка із контентом
│  │  │
│  │  ├─ 📁lesson/
│  │  │  ├─ [name].tsx // динамічний useRouter()
│  │  │  
│  │  ├─ 📁api/
│  │  │  ├─ lesson.ts // обробка http запитів
│  │
│  │
│  ├─ 📁styles/
│
│
├─ 📁public/

```

- - -
