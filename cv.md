Aynur Shauerman Junior Developer Resume
=======================================

**Name**: Aynur Shauerman, 32 years old

**Contacts**:
- [@Sib_aynur](https://t.me/Sib_aynur),
- <aykuli@ya.ru>,
- <https://github.com/aykuli>


**About me**: I like coding. It's appropriate extend from my love to mathematic. I started learning coding while being in parental leave. I started learning JavaScript first. Then I learn HTML, CSS, GIT, preprocessors, task-runners, bundlers. Everything is so interesting, so I want to code and learn everytime. This is my passion.

|**Languages**: | **Version control**:  | Frameworks, methodoligies | Tools                 |
| ------------- | --------------------  | ------------------------  | -------------------   |
| JavaScript    | Git                   | Sass/Scss                 | Visual Studio Code    |
| HTML/CSS      |                       | Pug                       | Sublime               |
| Python        |                       | Gulp                      | Photoshop             |
|               |                       | BEM                       | Figma                 |

[**Portfolio** on GitHub pages](https://aykuli.github.io/)

** Education**
   
[x] *HTMLAcademy.ru*
- [Профессиональный онлайн‑курс HTML и CSS, уровень 1](https://htmlacademy.ru/intensive/htmlcss) (I don't payed for it, just download it from rutracker.org/ My mentor was my friend [Yulia Maximova](https://github.com/cybersunt) from Saint-Peterurg)
- [Профессиональный онлайн‑курс HTML и CSS, уровень 2](https://htmlacademy.ru/intensive/adaptive) (passing now)

[x] [freecodecamp.org](https://www.freecodecamp.org/aynur_shauerman):
- Responsive Web Design Certification (300 hours)
- Javascript Algorithms And Data Structures Certification (300 hours)
 
[x] [codeacademy.com](https://www.codecademy.com/users/aynurshauerman2519902566/achievements)
- Introduction to HTML
- Learn CSS
- Make a Website
- Learn Bootstrap

[x]  [www.futurelearn.com](https://www.futurelearn.com/certificates/neuizu4)
- Digital Skills_User Experience

[x] [Siberian State University of Telecommunication and Information Sciences](https://readera.org/spektralnye-sposoby-ocenki-napravlenija-istochnikov-signalov-v-adaptivnyh-14335004)
- Faculty of radioelectronics


**Code example**
### Cash Register from FreeCodeCamp
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
    