# nightmare-async-await

```javascript
let href = await $.evaluate(() => document.querySelector('#r1-0 a.result__a').href) // evaluate function a return promise
console.log(href) // waits until evaluate function end
```

```javascript
const Nightmare = require('nightmare');

// waits until every line process for run func

(async () => {
    for (let i = 0; i < 10; i++) { // loop 10 times
        const $ = Nightmare({ show: true }) // run new window when everytime return
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
