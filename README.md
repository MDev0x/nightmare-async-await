# nightmare-async-await

```javascript
let href = await $.evaluate(() => document.querySelector('#r1-0 a.result__a').href) // evaluate function is a return promise
console.log(href) // wait until evaluate function end
```

```javascript
const Nightmare = require('nightmare');

(async () => {
    for (let i = 0; i < 10; i++) {
        const $ = Nightmare({ show: true })
        await $.goto('https://duckduckgo.com')
        await $.type('#search_form_input_homepage', 'github nightmare')
        await $.click('#search_button_homepage')
        await $.wait('#r1-0 a.result__a')
        let href = await $.evaluate(() => document.querySelector('#r1-0 a.result__a').href)
        console.log(href)
        await $.end()
    }
})();
```
