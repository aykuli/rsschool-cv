Aynur Shauerman Junior Developer Resume
=======================================

1. Aynur Shauerman
2. [@Sib_aynur](https://t.me/Sib_aynur),
    <aykuli@ya.ru>
    <https://github.com/aykuli>
3. I like coding. It's appropriate extend from my love to mathematic. I was learning coding while being in parental leave.
4.  **Languages**: JavaScript vanilla, HTML, CSS, Python, assembler, C51 for Aduc microcontrollers.
    **Version control**: Git.
    **Frameworks, methodoligies**: Gulp, Sass, Pug, BEM.
    **Tools**: Visual Studio Code, Sublime. Phototshop.
5. ## Cash Register from FreeCodeCamp
**Task**: Design a cash register drawer function *checkCashRegister()* that accepts purchase price as the first argument (*price*), payment as the second argument (*cash*), and cash-in-drawer (*cid*) as the third argument.
*cid* is a 2D array listing available currency.
The *checkCashRegister()* function should always return an object with a *status* key and a *change* key.
Return *{status: "INSUFFICIENT_FUNDS", change: []}* if cash-in-drawer is less than the *change* due, or if you cannot return the exact change.
Return *{status: "CLOSED", change: [...]}* with cash-in-drawer as the value for the key change if it is equal to the change due.
Otherwise, return *{status: "OPEN", change: [...]}*, with the change due in coins and bills, sorted in highest to lowest order, as the value of the *change* key.

| Currency              | Unit	| Amount            |
| --------------------- | ----- | ----------------- |
| Penny	                | $0.01 | (PENNY)           |
| Nickel	            | $0.05 | (NICKEL)          |
| Dime	                | $0.1  | (DIME)            |
| Quarter	            | $0.25	| (QUARTER)         |
| Dollar	            | $1	| (DOLLAR)          |
| Five Dollars	        | $5	| (FIVE)            |
| Ten Dollars	        | $10	| (TEN)             |
| Twenty Dollars	    | $20   | (TWENTY)          |
| One-hundred Dollars   | $100  | (ONE HUNDRED)     |

**Code**:

    var denom = [
    { name: 'ONE HUNDRED', val: 100 },
    { name: 'TWENTY', val: 20 },
    { name: 'TEN', val: 10 },
    { name: 'FIVE', val: 5 },
    { name: 'ONE', val: 1 },
    { name: 'QUARTER', val: 0.25 },
    { name: 'DIME', val: 0.1 },
    { name: 'NICKEL', val: 0.05 },
    { name: 'PENNY', val: 0.01 },
    ];

    function checkCashRegister(price, cash, cid) {
    var output = { status: null, change: [] };
    var change = cash - price;
    var register = cid.reduce(
        function(acc, curr) {
        acc.total += curr[1];
        acc[curr[0]] = curr[1];
        return acc;
        }, { total: 0 });
        
    if (register.total === change) {
        output.status = 'CLOSED';
        output.change = cid;
        return output;
    }
    if (register.total < change) {
        output.status = 'INSUFFICIENT_FUNDS';
        return output;
    }
    var change_arr = denom.reduce(function(acc, curr) {
        var value = 0;
        while (register[curr.name] > 0 && change >= curr.val) {
        change -= curr.val;
        register[curr.name] -= curr.val;
        value += curr.val;
        change = Math.round(change * 100) / 100;
        }
        if (value > 0) {
        acc.push([curr.name, value]);
        }
        return acc;
    }, []);
    if (change_arr.length < 1 || change > 0) {
        output.status = 'INSUFFICIENT_FUNDS';
        return output;
    }
    output.status = 'OPEN';
    output.change = change_arr;
    return output;
    }

    checkCashRegister(19.5, 20, [
    ['PENNY', 1.01],
    ['NICKEL', 2.05],
    ['DIME', 3.1],
    ['QUARTER', 4.25],
    ['ONE', 90],
    ['FIVE', 55],
    ['TEN', 20],
    ['TWENTY', 60],
    ['ONE HUNDRED', 100],
    ]);

6. [Portfolio page on GitHub pages](https://aykuli.github.io/)
7. -[x] [Профессиональный онлайн‑курс HTML и CSS, уровень 1](https://htmlacademy.ru/intensive/htmlcss) (I don't payed for it, just download it from rutracker.org/ Me mentor was my friend [Yulia Maximova](https://github.com/cybersunt) from Saint-Peterurg)
   -[x] [Профессиональный онлайн‑курс HTML и CSS, уровень 2](https://htmlacademy.ru/intensive/adaptive) (passing now)
   - [x] [Courses on freecodecamp.org](https://aykuli.github.io/certificates.html):
     - [x]  Responsive Web Design Certification (300 hours)
     - [x]  Javascript Algorithms And Data Structures Certification (300 hours)
   - [x]  Introduction to HTML from codeacademy.com
   - [x]  Learn CSS
   - [x]  Make a Website
   - [x]  Learn Bootstrap
   - [x]  [Digital Skills_User Experience from www.futurelearn.com](https://www.futurelearn.com/courses/digital-skills-user-experience)
9.  English intermediate. Reading datasheets, documentations and talking english.