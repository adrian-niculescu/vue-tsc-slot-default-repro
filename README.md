# vue-tsc 3.3.14: slot parameter default breaks codegen

A slot parameter with a default (`#toolbar="slotProps = {}"`) produces invalid generated code when the same template reads a property of an imported binding (`{{ KEYS.MORE }}`). vue-tsc then reports syntax errors and stops semantic checking for the whole program.

```sh
npm install
npm run type-check
```

Expected (vue-tsc 3.3.13), only the deliberate error in `src/other.ts`:

```
src/other.ts(1,14): error TS2322: Type 'string' is not assignable to type 'number'.
```

Actual (vue-tsc 3.3.14):

```
src/App.vue(8,39): error TS1005: ',' expected.
src/App.vue(8,41): error TS1181: Array element destructuring pattern expected.
```

Removing either `= {}` or `.MORE` from `src/App.vue` makes it pass. So does `npm install -D vue-tsc@3.3.13`.
