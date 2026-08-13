# Chapter 1 Intorduction

## TypeScript क्या है?
- TypeScript, JavaScript का ही एक extended/superset version है।
- यानी TypeScript में JavaScript के सारे basic features होते हैं, लेकिन इसके ऊपर कुछ extra features भी मिलते हैं—सबसे important है Types।

**`उदाहरण के लिए JavaScript में:`**

<code><pre>
function calculatePrice(inputPrice) {
    return inputPrice * 2;
}
</pre></code>
- यहाँ JavaScript को यह पता नहीं होता कि inputPrice number है, string है या कुछ और।

- लेकिन TypeScript में हम बता सकते हैं:
<code><pre>
function calculatePrice(inputPrice: number) {
    return inputPrice * 2;
}
</pre></code>

**यहाँ: `inputPrice: number`**
- का मतलब है कि **`inputPrice`** में सिर्फ number value आनी चाहिए।
- अगर हम ऐसा करें: **`calculatePrice("100");`** तो TypeScript error दिखाएगा क्योंकि "100" एक string है, जबकि function को number चाहिए।

## TypeScript में Static & Strict Typing
- TypeScript का सबसे बड़ा फायदा है कि यह हमें पहले ही बता देता है कि कहीं गलत type की value तो इस्तेमाल नहीं हो रही।

**`उदाहरण:`**
<code><pre>
let age: number = 25;

age = "twenty five"; // Error
</pre></code>

- क्योंकि age को हमने number बनाया है और उसमें string नहीं डाल सकते।
- JavaScript में ऐसी चीजें आसानी से हो सकती हैं, लेकिन TypeScript development के दौरान ही warning/error दे देता है।

## TypeScript को JavaScript Superset क्यों कहते हैं?
- क्योंकि TypeScript में valid JavaScript code भी valid होता है।
**`मतलब:`**
<code><pre>
const name = "Jyoti";

console.log(name);
</pre></code>

- यह JavaScript है और TypeScript में भी चल सकता है।
- लेकिन TypeScript में हम extra type information भी जोड़ सकते हैं:

<code><pre>
const name: string = "Jyoti";
</pre></code>

## अब सबसे important सवाल: TypeScript क्यों इस्तेमाल करें?

- TypeScript का मुख्य फायदा है बड़े projects को safer और easier to maintain बनाना।

- मान लीजिए आपकी application बहुत बड़ी है और उसमें 50 developers काम कर रहे हैं।

**`एक function है:`**
<code><pre>
function addPrice(price: number) {
    return price + 100;
}
</pre></code>

- अब अगर कोई developer गलती से:
<code><pre>
addPrice("500");
</pre></code>

- लिख देता है, तो TypeScript तुरंत error दिखा देगा। इससे bugs कम होते हैं।

## TypeScript के मुख्य फायदे
**1. Type Safety**
- गलत type की value देने पर पहले ही error मिल जाता है।

**2. Better Code Quality**
- Code ज्यादा predictable और organized रहता है।

**3. Better IDE Support**
- VS Code आपको autocomplete, suggestions और errors बेहतर तरीके से दिखाता है।

**4. Large Projects के लिए Useful**
- बड़ी applications में code maintain करना आसान होता है।

**5. Refactoring आसान होता है**
- अगर किसी variable/function का नाम या structure बदलना हो तो TypeScript errors के जरिए पता लगाने में मदद करता है कि कहाँ-कहाँ बदलाव करना है।

**6. JavaScript Knowledge बेकार नहीं जाता**
- क्योंकि TypeScript JavaScript का replacement नहीं बल्कि उसका superset है।

## TypeScript की सबसे बड़ी limitation
- TypeScript code सीधे browser में run नहीं होता।
- मान लो आपके पास: **`calculator.ts`** है।
- Browser इस **`.ts`** file को directly execute नहीं कर सकता।
- Browser को चाहिए: **`JavaScript`** इसलिए हमें: **`Compile`** करना पड़ता है।
<code><pre>
TypeScript (.ts)
       ↓
   Compile
       ↓
JavaScript (.js)
       ↓
    Browser
</pre></code>

## Compilation क्या है?

- Compilation का मतलब है: TypeScript code को JavaScript code में convert करना।

**`Example:`**

<code><pre>
function calculate(price: number) {
    return price + 100;
}
</pre></code>

- Compiler इसे JavaScript में convert करेगा:

<code><pre>
function calculate(price) {
    return price + 100;
}
</pre></code>

- ध्यान दें कि: **`: number`** हटा दिया गया। क्योंकि **`: number`** TypeScript-specific syntax है और browser इसे नहीं समझता।

## TypeScript Compiler क्या करता है?

- TypeScript में एक tool होता है:
- TypeScript Compiler जिसे **`commonly: tsc`** कहा जाता है।
- इसका काम: **`.ts → .js`** करना है।

## TypeScript Compiler install करने के लिए क्या चाहिए?
- TypeScript compiler install करने के लिए आमतौर पर Node.js + npm का इस्तेमाल किया जाता है।
- **`npm = Node Package Manager`**
- यह Node.js के साथ आता है और JavaScript/TypeScript packages install करने के लिए इस्तेमाल होता है।

- पहले Node.js install करना होता है।

**`फिर terminal में:`** 
<code><pre>
npm install -g typescript
</pre></code>

terminal में project folder के अंदर जाकर **`tsc calculator.ts`**

<code><pre>
calculator.ts
       ↓
calculator.js
</pre></code>

## फिर Browser में कौन-सी file चलाएँगे

**`Browser में:`**

❌ यह नहीं:

`<script src="calculator.ts"></script>`

बल्कि compiled JavaScript:

`<script src="calculator.js"></script>`

क्योंकि browser JavaScript को समझता है।

**`पूरा flow:`**

<code><pre>
calculator.ts
      ↓
    tsc
      ↓
calculator.js
      ↓
   HTML
      ↓
  Browser
</pre></code>

- **`Note :`**  बड़े Project में manually tsc नहीं चलाएँगे

**`मान लो project में:`**
<code><pre>
user.ts
product.ts
cart.ts
payment.ts
order.ts
</pre></code>

- 100 TypeScript files हैं।

**`आप हर file के लिए:`**

<code><pre>
tsc user.ts
tsc product.ts
tsc cart.ts
...
</pre></code>

- नहीं करेंगे। बड़े projects में compilation process automate किया जाता है।

