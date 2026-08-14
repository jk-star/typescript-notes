# Chapter 2 TypeScript Data Types

- TypeScript me **Data Types** ka use ye batane ke liye hota hai ki kisi variable me kis type ki value store hogi.

## 1. **`string`**

- Text/string value ke liye use hota hai.

```ts
let userName: string = "Jyoti";
let message: string = "Hello TypeScript";

console.log(userName);
console.log(message);
```

- ❌ Ye allowed nahi hai:

```ts
let userName: string = 100;
```

---

## 2. **`number`**

- Numbers ke liye use hota hai — integer aur decimal dono.

```ts
let age: number = 25;
let price: number = 499.99;

console.log(age);
console.log(price);
```

```ts
let total: number = 100 + 50;
```

---

## 3. `boolean`

- Sirf **`true`** ya **`false`** value store karta hai.

```ts
let isLoggedIn: boolean = true;
let isAdmin: boolean = false;

console.log(isLoggedIn);
console.log(isAdmin);
```

**Real-life Example**

```ts
let isOnline: boolean = true;

if (isOnline) {
  console.log("User Online hai");
}
```

---

## 4. `null`

- **`null`** ka matlab hai **intentionally koi value nahi hai**.

```ts
let selectedUser: null = null;
```

**Real-life Example**

```ts
let profileImage: string | null = null;

profileImage = "profile.jpg";
```

- Yaha **`profileImage`** initially **`null`** hai, baad me string ho sakta hai.

---

## 5. `undefined`

- Jab variable ko value assign nahi ki gayi ho, tab **`undefined`** mil sakta hai.

```ts
let userEmail: undefined = undefined;
```

**Example**

```ts
let userName: string | undefined;

userName = "Jyoti";
```

---

## 6. `any`

- **`any`** ka matlab hai TypeScript **type checking ko practically disable** kar deta hai.

```ts
let value: any = "Hello";

value = 100;
value = true;
value = [];
```

- Sab allowed hai.

- > ⚠️ **`any`** ka unnecessary use avoid karna chahiye kyunki TypeScript ka main benefit hi type safety hai.

---

## 7. `unknown`

- **`unknown`** bhi kisi bhi type ki value accept kar sakta hai, lekin `any` ke comparison me **zyada safe** hai.

```ts
let value: unknown = "Hello";

value = 100;
value = true;
```

- Lekin directly methods/properties use nahi kar sakte:

```ts
let value: unknown = "Hello";

// value.toUpperCase(); ❌
```

- Pehle type check karna padega:

```ts
if (typeof value === "string") {
  console.log(value.toUpperCase());
}
```

## Simple Difference

```text
any     → kuch bhi karo, TypeScript check nahi karega
unknown → use karne se pehle type check karo
```

---

## 8. `void`

- `void` mostly un functions ke liye use hota hai jo **kuch return nahi karte**.

```ts
function greet(): void {
  console.log("Hello Jyoti");
}
```

**Function call:**

```ts
greet();
```

- Yaha function sirf kaam kar raha hai, koi value return nahi kar raha.

---

## 9. `never`

- **`never`** ka use aise cases me hota hai jahan function **kabhi normally complete nahi hota**.

**Example: Error Throw Karna**

```ts
function throwError(message: string): never {
  throw new Error(message);
}
```

## Infinite Loop

```ts
function infiniteLoop(): never {
  while (true) {
    console.log("Running...");
  }
}
```

## `void` vs `never`

```text
void   → function complete ho sakta hai, but value return nahi karta

never  → function normally complete hi nahi hota
```

---

## 10. Arrays

- Array me same type ki multiple values store kar sakte hain.

**Syntax 1**

```ts
let numbers: number[] = [10, 20, 30, 40];
```

**Syntax 2**

```ts
let numbers: Array<number> = [10, 20, 30, 40];
```

## String Array

```ts
let fruits: string[] = ["Apple", "Mango", "Banana"];
```

## Boolean Array

```ts
let status: boolean[] = [true, false, true];
```

## Multiple Types

```ts
let data: (string | number)[] = ["Jyoti", 25, "Developer"];
```

---

## 11. Tuples

- Tuple ek **fixed structure/position wala array** hota hai.

```ts
let user: [string, number] = ["Jyoti", 25];
```

**Yaha:**

```text
index 0 → string
index 1 → number
```

**Ye galat hai:**

```ts
let user: [string, number] = [25, "Jyoti"]; // ❌
```

## Real-life Example

```ts
let product: [string, number, boolean] = [
  "Laptop",
  50000,
  true
];
```

**Meaning:**

```text
Product Name → string
Price        → number
Available    → boolean
```

---

## 12. Enums

- **`enum`** ka use **fixed named values** define karne ke liye hota hai.

```ts
enum Role {
  Admin,
  User,
  Guest
}

let userRole: Role = Role.Admin;

console.log(userRole);
```

## String Enum

```ts
enum Status {
  Success = "SUCCESS",
  Error = "ERROR",
  Loading = "LOADING"
}

let currentStatus: Status = Status.Success;

console.log(currentStatus);
```

**Real-life Example**

```ts
enum PaymentStatus {
  Pending = "PENDING",
  Paid = "PAID",
  Failed = "FAILED"
}

let payment: PaymentStatus = PaymentStatus.Paid;
```

---

## Quick Revision

| Type | Meaning |
|---|---|
| `string` | Text |
| `number` | Number |
| `boolean` | `true` / `false` |
| `null` | Intentionally empty value |
| `undefined` | Value not assigned |
| `any` | Any type, no strict checking |
| `unknown` | Any type, but type-check required |
| `void` | Function returns nothing |
| `never` | Function never normally completes |
| `Array` | Multiple values |
| `Tuple` | Fixed-position values |
| `Enum` | Fixed named values |
