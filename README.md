# Kalkulyator-Funksiyalari-Test-To-plami-Jest-
/**
 * Kalkulyator moduli
 * Asosiy arifmetik amallar va kengaytirilgan funksiyalar
 */

function add(a, b) {
    return a + b;
}

function subtract(a, b) {
    return a - b;
}

function multiply(a, b) {
    return a * b;
}

function divide(a, b) {
    if (b === 0) {
        throw new Error("Nolga bo'lish mumkin emas");
    }
    return a / b;
}

function power(base, exp) {
    return Math.pow(base, exp);
}

function sqrt(n) {
    if (n < 0) {
        throw new Error("Manfiy sondan kvadrat ildiz chiqarib bo'lmaydi");
    }
    return Math.sqrt(n);
}

module.exports = {
    add,
    subtract,
    multiply,
    divide,
    power,
    sqrt
};
```eof

I will now generate the `calculator.test.js` test suite file.

```javascript:calculator.test.js
const { add, subtract, multiply, divide, power, sqrt } = require('./calculator');

describe("Kalkulyator Moduli Testlari", () => {
    
    describe("add funksiyasi", () => {
        test("ikkita musbat sonni qo'shish", () => {
            expect(add(2, 3)).toBe(5);
        });

        test("musbat va manfiy sonlarni qo'shish", () => {
            expect(add(10, -4)).toBe(6);
        });

        test("nol bilan qo'shish", () => {
            expect(add(0, 7)).toBe(7);
        });

        test("chegara qiymatlari bilan qo'shish (Number.MAX_SAFE_INTEGER)", () => {
            expect(add(Number.MAX_SAFE_INTEGER, 0)).toBe(Number.MAX_SAFE_INTEGER);
        });
    });

    describe("subtract funksiyasi", () => {
        test("musbat sonlarni ayirish", () => {
            expect(subtract(10, 4)).toBe(6);
        });

        test("manfiy natija beruvchi ayirish", () => {
            expect(subtract(3, 8)).toBe(-5);
        });

        test("noldan sonni ayirish", () => {
            expect(subtract(0, 5)).toBe(-5);
        });
    });

    describe("multiply funksiyasi", () => {
        test("ikkita musbat sonni ko'paytirish", () => {
            expect(multiply(4, 5)).toBe(20);
        });

        test("nolga ko'paytirish", () => {
            expect(multiply(123, 0)).toBe(0);
        });

        test("manfiy sonlarni ko'paytirish", () => {
            expect(multiply(-3, -4)).toBe(12);
        });
    });

    describe("divide funksiyasi", () => {
        test("oddiy bo'lish amali", () => {
            expect(divide(10, 2)).toBe(5);
        });

        test("kasr natija beruvchi bo'lish", () => {
            expect(divide(5, 2)).toBe(2.5);
        });

        test("0 ga bo'lganda Error tashlash", () => {
            expect(() => divide(5, 0)).toThrow("Nolga bo'lish mumkin emas");
        });

        test("manfiy sonni bo'lish", () => {
            expect(divide(-10, 2)).toBe(-5);
        });
    });

    describe("power funksiyasi", () => {
        test("musbat son darajasi", () => {
            expect(power(2, 3)).toBe(8);
        });

        test("nol darajasi 1 ga teng", () => {
            expect(power(5, 0)).toBe(1);
        });

        test("manfiy daraja", () => {
            expect(power(2, -2)).toBe(0.25);
        });
    });

    describe("sqrt funksiyasi", () => {
        test("musbat sondan ildiz chiqarish", () => {
            expect(sqrt(9)).toBe(3);
        });

        test("nol dan ildiz chiqarish", () => {
            expect(sqrt(0)).toBe(0);
        });

        test("manfiy sondan ildiz chiqarganda Error tashlash", () => {
            expect(() => sqrt(-4)).toThrow("Manfiy sondan kvadrat ildiz chiqarib bo'lmaydi");
        });
    });

});
```eof

### 💡 Qo'llanma:
1. `package.json` faylingizda test skripti to'g'ri sozlanganligiga ishonch hosil qiling (`"test": "jest"`).
2. Terminalda `npm test` buyrug'ini ishga tushiring va barcha testlar muvaffaqiyatli (yashil rangda) o'tishini kuzating. Jami 20 ta test barcha talab qilingan edge-case'larni to'liq qamrab oladi!
