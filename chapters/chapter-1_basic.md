# Chapter 1 TypeScript Basics

## 1. What is TypeScript?

- TypeScript ek programming language hai jo JavaScript ke upar build ki
gayi hai.

**Simple words mein:**

- TypeScript = JavaScript + Type Safety + Extra Features

**JavaScript mein:**

``` js
let age = 25;

age = "twenty five";
```

- JavaScript isse allow kar deta hai kyunki JavaScript dynamically typed
language hai.

**TypeScript mein:**

``` ts
let age: number = 25;

age = "twenty five"; // ❌ Error
```

- TypeScript hume batata hai: > "Bhai, `age` number hai, string nahi." 😄

## 2. TypeScript ka main purpose

- TypeScript ka main purpose hai **code mein errors ko early detect
karna**, especially large projects mein.

**Example:**

``` ts
function add(a: number, b: number): number {
    return a + b;
}

add(10, 20);       // ✅
add("10", "20");   // ❌ Error
```

- TypeScript development ke time hi warning de deta hai.

------------------------------------------------------------------------

## 3. TypeScript vs JavaScript

  | JavaScript                         | TypeScript                                   |
| ---------------------------------- | -------------------------------------------- |
| Dynamically typed                  | Statically typed                             |
| Browser directly run kar sakta hai | Usually JS mein compile hota hai             |
| Type checking limited              | Strong type checking                         |
| `.js` file                         | `.ts` file                                   |
| Small projects ke liye easy        | Large projects ke liye useful                |
| Runtime errors comparatively zyada | Development-time errors detect kar sakta hai |
| Simple syntax                      | JS + additional features                     |


**`JavaScript`**

``` js
let username = "Jyoti";

username = 100;
```

- JavaScript mein allowed hai.

**`TypeScript`**

``` ts
let username: string = "Jyoti";

username = 100; // ❌ Error
```

- TypeScript kahega: Type 'number' is not assignable to type 'string'


**`Important Point`**

- TypeScript **JavaScript ko replace nahi karta**.

**`Actually:`**

``` text
TypeScript
    ↓
Compile / Transpile
    ↓
JavaScript
    ↓
Browser / Node.js
```

- Browser normally TypeScript ko directly execute nahi karta.

------------------------------------------------------------------------

## 4. Installation & `tsconfig.json`

- TypeScript use karne ke liye Node.js installed hona useful hai.

**Check Node.js:**

``` bash
node -v
```

**Check npm:**

``` bash
npm -v
```

**TypeScript globally install:**

``` bash
npm install -g typescript
```

**Version check:**

``` bash
tsc -v
```

**Project ke andar TypeScript install karna:**

``` bash
npm install -D typescript
```

**`tsconfig.json` create karne ke liye:**

``` bash
npx tsc --init
```

**Isse project mein:**

``` text
tsconfig.json
```

- file create hoti hai.

------------------------------------------------------------------------

## 5. `tsconfig.json` kya hai?

- **`tsconfig.json`** TypeScript compiler ki **configuration file** hai.

**Simple words:**

- > **`tsconfig.json`** TypeScript compiler ko batata hai ki TypeScript code
> ko kaise compile karna hai.

**Example:**

``` json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "strict": true,
    "outDir": "./dist"
  }
}
```

**Important Options**

- **`target`** Batata hai ki JavaScript kis version mein generate karna hai.

``` json
"target": "ES2020"
```

- **`module`** Module system define karta hai.

``` json
"module": "commonjs"
```

**Ya modern projects mein:**

``` json
"module": "ESNext"
```

- **`strict`** Strict type checking enable karta hai.

``` json
"strict": true
```

- Generally ye recommended hai.

- **`outDir`** Compiled JavaScript files kahan jayengi:

``` json
"outDir": "./dist"
```

**Example:**

``` text
src/
   app.ts

dist/
   app.js
```

------------------------------------------------------------------------

## 6. Type Annotations

- **Type annotation** ka matlab hai variable/function ko explicitly batana
ki uska type kya hai.

**Syntax:**

``` ts
let variableName: type = value;
```

**String**

``` ts
let name: string = "Jyoti";
```

**Number**

``` ts
let age: number = 25;
```

**Boolean**

``` ts
let isLoggedIn: boolean = true;
```

**Array**

``` ts
let fruits: string[] = ["Apple", "Mango", "Banana"];
```

**Numbers:**

``` ts
let marks: number[] = [80, 90, 75];
```

**Object**

``` ts
let user: {
    name: string;
    age: number;
} = {
    name: "Jyoti",
    age: 25
};
```

------------------------------------------------------------------------

## 7. Function Type Annotation

- Function parameters ka type bhi define kar sakte hain:

``` ts
function add(a: number, b: number) {
    return a + b;
}
```

**Yahan:**

``` ts
a: number
b: number
```

- ka matlab hai **`a`** aur **`b`** numbers hone chahiye.

- Return type bhi define kar sakte hain:

``` ts
function add(a: number, b: number): number {
    return a + b;
}
```

**Yahan:**

``` ts
: number
```

- batata hai ki function **number return karega**.

------------------------------------------------------------------------

## 8. Type Inference

- TypeScript mein har jagah type likhna zaroori nahi hai.

- TypeScript khud bhi type **infer** kar sakta hai.

**Example:**

``` ts
let name = "Jyoti";
```

**TypeScript automatically samajh lega:**

``` text
name → string
```

**Similarly:**

``` ts
let age = 25;
```

**TypeScript infer karega:**

``` text
age → number
```

**And:**

``` ts
let isAdmin = true;
```

**TypeScript samajh jayega:**

``` text
isAdmin → boolean
```

- Isliye ye dono valid hain:

**Explicit type:**

``` ts
let age: number = 25;
```

**Type inference:**

``` ts
let age = 25;
```

- Usually simple variables mein **type inference use karna clean
approach** hota hai.

------------------------------------------------------------------------

## 9. Type Annotation vs Type Inference

**Type Annotation**

- Hum khud type batate hain:

``` ts
let username: string = "Jyoti";
```

**Type Inference**

- TypeScript khud type samajhta hai:

``` ts
let username = "Jyoti";
```

**Dono mein:**

``` text
username → string
```

------------------------------------------------------------------------

## 10. Compile TypeScript → JavaScript

- Ye TypeScript ka bahut important concept hai.

**Maan lo file hai:**

``` text
app.ts
```

**Code:**

``` ts
let name: string = "Jyoti";

console.log(name);
```

**TypeScript compiler run karo:**

``` bash
tsc app.ts
```

Flow:

``` text
app.ts
  ↓
TypeScript Compiler
  ↓
app.js
```

Generated JavaScript:

``` js
let name = "Jyoti";

console.log(name);
```

- **Notice karo : `string`** JavaScript mein nahi hai.

------------------------------------------------------------------------

## 11. Full Practical Flow

- Ek simple TypeScript project ka flow:

``` text
my-project/
│
├── src/
│   └── app.ts
│
├── dist/
│   └── app.js
│
├── package.json
└── tsconfig.json
```

**`app.ts`:**

``` ts
function greet(name: string): string {
    return `Hello ${name}`;
}

console.log(greet("Jyoti"));
```

**Compile:**

``` bash
tsc
```

**Output:**

``` text
dist/app.js
```

**Generated JavaScript:**

``` js
function greet(name) {
    return `Hello ${name}`;
}

console.log(greet("Jyoti"));
```

------------------------------------------------------------------------

## 🔥 Quick Revision

Yaad rakhne ke liye:

``` text
TypeScript
   ↓
JavaScript ka superset
   ↓
Type Safety
   ↓
.ts file
   ↓
tsc compiler
   ↓
.js file
   ↓
Browser / Node.js
```

## Most Important Commands

``` bash
npm install -D typescript
```

``` bash
npx tsc --init
```

``` bash
tsc app.ts
```

``` bash
tsc
```

## Most Important Concepts

``` text
Type Annotation
      ↓
let age: number = 25;

Type Inference
      ↓
let age = 25;

Compile
      ↓
.ts → .js

Configuration
      ↓
tsconfig.json
```

