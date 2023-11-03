# TypeScript

> значно підвищує читабельність, якість коду та відловлює значну кількість помилок ще на етапі написання

1. створюємо директорію, наприклад **ts-eslint**
2. ініціалізуємо проект: ``npm init -y``
3. додаємо пакет TS: ``npm install typescript --save-dev``
4. створюємо конфігураційний файл tsconfig.json: ``npx tsc --init``
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

5. встановлюємо статичний аналізатор JS коду: ``npm i eslint -D``
    + ``@typescript-eslint/parser`` - парсер що дає змогу ESLint розуміти TS код;
    + ``@typescript-eslint/eslint-plugin`` - плагін з рекомендованими правилами для TS синтаксису;



