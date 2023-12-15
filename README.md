# NEXT-frontend

- _it is maintained by Vercel_
- _deploy full-stack app to any Node.js or serverless hosting_
- _static app can be deployed to any static hosting_

## Theory

### next-env.d.ts
  - призначений для визначення типів, які можуть бути використані в проекті;
  - автоматично включається Next.js під час створення нового проекту з TypeScript;
  - у ньому можна визначити свої типи або використовувати типи з залежностей;
  - використовується для покращення автодоповнення та роботи інструментів розробки;

Файл **next-env.d.ts** зазвичай не потребує багато змін, оскільки він включає важливі посилання на типи, необхідні для коректної роботи Next.js із TypeScript. Ось кілька можливих доповнень, які розробники можуть вносити:

Якщо ви використовуєте сторонні бібліотеки, які не мають визначених типів у власних файлів **@types**, ви можете додати посилання на відповідні типи прямо у цей файл.

```tsx
  /// <reference types="next" />
  /// <reference types="next/image-types/global" />
  /// <reference types="@types/my-library" />
```

Якщо у вас є глобальні типи або змінні, які використовуються в усьому проекті, ви можете додати їх в цей файл.

```tsx
  /// <reference types="next" />
  /// <reference types="next/image-types/global" />

  declare module 'global-types' {
    interface MyGlobalType {
      // ваші глобальні типи тут
    }

    const myGlobalVariable: string;

    export { MyGlobalType, myGlobalVariable };
  }
```

Якщо ви змінюєте або розширюєте конфігурацію Next.js, наприклад, додаючи нові плагіни, ви можете додати відповідні типи для цих змін.

```tsx
  /// <reference types="next" />
  /// <reference types="next/image-types/global" />

  declare module 'next' {
    interface NextConfig {
      // ваші зміни у конфігурації Next.js тут
    }
  }
```

> Необхідність у цих доповненнях залежить від конкретних потреб вашого проекту. Зазвичай багато проектів можуть працювати з базовим вмістом next-env.d.ts без додаткових змін. Якщо ви вносите зміни, будьте обережні і переконайтеся, що вони не порушують стандартну функціональність Next.js та TypeScript.













- - -

## YouTube Next

* [Все про Next.JS - для початківців і не тільки](https://www.youtube.com/playlist?list=PLx9b8ngesbGEtYSFwh61bq1h7B4rmVqWT)
  - _Огляд Next.JS за 16 хвилин_ 👁
  - _Велике оновлення NextJS 13.4 - короткий огляд_ 👁
  - _нові серверні компонети 13.4 - навіщо потрібні_ 👁
* [NextJS 13](https://www.youtube.com/playlist?list=PLiZoB8JBsdzlgeYHZDJ_orG0vy8JiEhKr)
  - 🤖 **Михаил Непомнящий** 💥
  - _Быстрый старт_ 👁
  - _Использование клиентских компонентов_ 👁
    + https://github.com/michey85/next-blog-app
  - _API эндпойнты в NextJS 13_ 👁
    + https://github.com/michey85/next-blog-app/tree/api-points-basics
  - _Аутентификация и приватные роуты_ 👁
    + https://github.com/michey85/next-blog-app/tree/auth
  - _Варианты рендеринга - RSC, CSR, SSR, SSG, ISR_ 🧑‍💻
  - _Оптимизация изображений_ 🧑‍🎨
  - Релиз NextJS 14 и Server actions
    + https://github.com/michey85/next-blog-app/tree/next14

- - -

## [NEXT](https://nextjs.org/) - The React Framework for the Web
> &emsp;_Used by some of the world's largest companies, Next.js enables you to create full-stack Web applications by extending the latest React features, and integrating powerful Rust-based JavaScript tooling for the fastest builds._





- - -

## TypeScript Links

_Typescript — це суперсет до JavaScript. Створена і зарелізана в 2012 році компанією Microsoft. Основним козирем мови є статична типізація, яка дозволяє JS код бути більш надійним._


### ARTICLES

* [TypeScript](https://www.gen.tech/post/typescript-vid-hajpu-do-standartu-rozrobki): від хайпу до стандарту розробки 👁
* [Interface vs Type різниця](https://medium.com/@jstify.community/interface-vs-type-b49b8403bb9c) 🤦
* [Підвищуємо якість коду за допомогою TypeScript, ESLint та Prettier.](https://medium.com/@jstify.community/%D0%BF%D1%96%D0%B4%D0%B2%D0%B8%D1%89%D1%83%D1%94%D0%BC%D0%BE-%D1%8F%D0%BA%D1%96%D1%81%D1%82%D1%8C-%D0%BA%D0%BE%D0%B4%D1%83-%D0%B7%D0%B0-%D0%B4%D0%BE%D0%BF%D0%BE%D0%BC%D0%BE%D0%B3%D0%BE%D1%8E-typescript-eslint-%D1%82%D0%B0-prettier-f50493eba0bd) 🧑‍🌾

#### Dmitri Pavlutin
> &emsp;_helps developers understand Frontend technologies_

* REACT ARTICLES
  + [How to Write Comments in React](https://dmitripavlutin.com/react-comments/): The Good, the Bad and the Ugly
  + [React forwardRef()](https://dmitripavlutin.com/react-forwardref/): How to Pass Refs to Child Components
* TypeScript ARTICLES
  + [Record Type in TypeScript](https://dmitripavlutin.com/typescript-record/): A Quick Intro
  + TypeScript [Function Overloading](https://dmitripavlutin.com/typescript-function-overloading/)

- - -

### YouTube TypeScript

* [TypeScript для початківців](https://www.youtube.com/watch?v=ND-XaEQ4VSk)
* [The Complete Guide to Immutability in TypeScript](https://levelup.gitconnected.com/the-complete-guide-to-immutability-in-typescript-99154f859fdb)
  - _Immutability in JavaScript_
  - _Immutability in TypeScript_
  - _Guidelines for Immutability_
* [How To Create An Advanced Shopping Cart](https://www.youtube.com/watch?v=lATafp15HWA&t=4s) With React and TypeScript


TypeScript став потужною мовою в сучасному середовищі розробки, пропонуючи розробникам ряд переваг для підвищення продуктивності, якості коду та зручності обслуговування. Використовуючи TypeScript, розробники можуть завчасно виявляти помилки, покращувати співпрацю та створювати більш надійні програми. 

- - -
