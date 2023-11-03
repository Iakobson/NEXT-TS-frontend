# TypeScript

> значно підвищує читабельність, якість коду та відловлює значну кількість помилок ще на етапі написання

1. створюємо директорію, наприклад **ts-eslint**
2. ініціалізуємо проект: ``npm init -y``
3. додаємо пакет TS: ``npm install typescript --save-dev``
4. додаємо пакет запуску коду: ``npm install ts-node -D``
5. створюємо конфігураційний файл tsconfig.json: ``npx tsc --init``
    + ```go
      {
        "compilerOptions": {
          /* Language and Environment */
          "target": "esnext",
          "module": "esnext",
          "outDir": "./dist",
          /* Type Checking */
          "strict": true,
          "noImplicitReturns": true
      },
       "include": [ "src/*.ts"],
        "exclude": [ "node_modules" ]
      }
      ```

> налаштуваннях компіляції TS: https://www.typescriptlang.org/tsconfig \
> поексперементувати з пропертями: https://www.typescriptlang.org/play?q=404#example/union-and-intersection-types

6. встановлюємо статичний аналізатор JS коду: ``npm i eslint -D``
    + ``npm i @typescript-eslint/parser -D`` - парсер що дає змогу ESLint розуміти TS код;
    + ``npm i @typescript-eslint/eslint-plugin -D`` - плагін з рекомендованими правилами для TS синтаксису;
7. необхідний конфігураційний файл .eslintrc: ``npm init @eslint/config``


