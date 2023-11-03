# TypeScript

> значно підвищує читабельність, якість коду та відловлює значну кількість помилок ще на етапі написання

1. створюємо директорію, наприклад **ts-eslint**
2. ініціалізуємо проект: ``npm init -y``
3. додаємо пакет TS: ``npm install typescript --save-dev``
4. створюємо конфігураційний файл tsconfig.json: ``npx tsc --init``

```go
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







