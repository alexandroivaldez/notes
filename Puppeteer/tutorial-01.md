# Setup

Puppeteer can be used in VSCode or any other IDE of your choice.

Installing puppeteer

```shell
npm i puppeteer --save
```

Run Node.js

```shell
npm init -y
```


Basic Puppeteer Script

```js
// index.js
const puppeteer = require('puppeteer');

(async () => {
    const browser = await puppeteer.launch();
    const page = await browser.newPage();
    await page.goto('https://example.com');
    await page.screenshot({ path: 'example.png' });

    await browser.close();
})
```

Run Basic Script

```shell
node .\index.js
```
