
[![ajs](http://i.imgur.com/nQiOz0E.png)](#)

# `$ ajs`

 [![Support me on Patreon][badge_patreon]][patreon] [![Buy me a book][badge_amazon]][amazon] [![PayPal][badge_paypal_donate]][paypal-donations] [![Version](https://img.shields.io/npm/v/ajs.svg)](https://www.npmjs.com/package/ajs) [![Downloads](https://img.shields.io/npm/dt/ajs.svg)](https://www.npmjs.com/package/ajs)

> Asynchronous templating in Node.js

## Features

 - Control flow with `<% %>`
 - Escaped output with `<%= %>` (escape function configurable)
 - Unescaped raw output with `<%- %>`
 - Newline-trim mode ('newline slurping') with `-%>` ending tag
 - Custom delimiters (e.g., use `<? ?>` instead of `<% %>`)
 - Includes
 - Static caching of intermediate JavaScript
 - Static caching of templates
 - Complies with the [Express](http://expressjs.com) view system


## :cloud: Installation

You can install the package globally and use it as command line tool:


```sh
$ npm i -g ajs
```


Then, run `ajs --help` and see what the CLI tool can do.


```
$ ajs --help
Usage: ajs [options]

Asynchronous templating in Node.js

Options:
  -t, --tree             Output the abstract syntax tree
  -s, --source           Output the raw VM source
  -l, --locals <locals>  The template data as JSON.
  -v, --version          Displays version information.
  -h, --help             Displays this help.

Examples:
  $ ajs template.ajs
  $ ajs -t template.ajs
  $ ajs -s template.ajs

Documentation can be found at https://github.com/IonicaBizau/ajs#readme.
```

## :clipboard: Example


Here is an example how to use this package as library. To install it locally, as library, you can do that using `npm`:

```sh
$ npm i --save ajs
```



```js
const ajs = require("ajs");

ajs.render(
`<% fruits.forEach(function (c) { -%>
<%= c %>s are great
<% }) %>`, {
    locals: {
        fruits: ["Apple", "Pear", "Orange"]
    }
}, (err, data) => {
    console.log(err || data);
    // =>
    // Apples are great
    // Pears are great
    // Oranges are great
});

// Do some async stuff
ajs.render(
`<% fetchData(function (err, msg) {
   if (err) { %>
     Error: <%= err.message %>
   <% } else {
    <%= msg %>
   <% } %>
<% }) %>`, {
    locals: {
        fetchData: cb => setTimeout(
            () => cb(null, "Hey there!")
          , 1000
        )
    }
}, (err, data) => {
    console.log(err || data);
    // =>
    // Hey there!
});
```



## :question: Get Help

There are few ways to get help:

 1. Please [post questions on Stack Overflow](https://stackoverflow.com/questions/ask). You can open issues with questions, as long you add a link to your Stack Overflow question.
 2. For bug reports and feature requests, open issues. :bug:
 3. For direct and quick help, you can [use Codementor](https://www.codementor.io/johnnyb). :rocket:


## :memo: Documentation

For full API reference, see the [DOCUMENTATION.md][docs] file.

## :yum: How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].


## :sparkling_heart: Support my projects

I open-source almost everything I can, and I try to reply everyone needing help using these projects. Obviously,
this takes time. You can integrate and use these projects in your applications *for free*! You can even change the source code and redistribute (even resell it).

However, if you get some profit from this or just want to encourage me to continue creating stuff, there are few ways you can do it:

 - Starring and sharing the projects you like :rocket:
 - [![PayPal][badge_paypal]][paypal-donations]—You can make one-time donations via PayPal. I'll probably buy a ~~coffee~~ tea. :tea:
 - [![Support me on Patreon][badge_patreon]][patreon]—Set up a recurring monthly donation and you will get interesting news about what I'm doing (things that I don't share with everyone).
 - **Bitcoin**—You can send me bitcoins at this address (or scanning the code below): `1P9BRsmazNQcuyTxEqveUsnf5CERdq35V6`

    ![](https://i.imgur.com/z6OQI95.png)

Thanks! :heart:


## :cake: Thanks

Big thanks to [Evan Owen](https://github.com/kainosnoema) who created the initial versions of the project! Amazing stuff! :cake:


## :dizzy: Where is this library used?
If you are using this library in one of your projects, add it in this list. :sparkles:


 - [`ajs-xgettext`](https://npmjs.com/package/ajs-xgettext) (by Duane Griffin)—Extract localised text from AJS templates
 - [`bloggify-ajs-renderer`](https://github.com/IonicaBizau/bloggify-ajs-renderer#readme)—ajs renderer for Bloggify.
 - [`bloggify-icons`](https://github.com/Bloggify/bloggify-icons#readme)—The Bloggify icons for the web.
 - [`express-ajs`](https://github.com/IonicaBizau/express-ajs#readme)—Minimal example of how to use ajs in Express.
 - [`git-stats-html`](https://github.com/IonicaBizau/git-stats-html#readme)—Turn git-stats result into HTML output.

## :scroll: License

[MIT][license] © [Ionică Bizău][website]

[badge_patreon]: http://ionicabizau.github.io/badges/patreon.svg
[badge_amazon]: http://ionicabizau.github.io/badges/amazon.svg
[badge_paypal]: http://ionicabizau.github.io/badges/paypal.svg
[badge_paypal_donate]: http://ionicabizau.github.io/badges/paypal_donate.svg
[patreon]: https://www.patreon.com/ionicabizau
[amazon]: http://amzn.eu/hRo9sIZ
[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RVXDDLKKLQRJW
[donate-now]: http://i.imgur.com/6cMbHOC.png

[license]: http://showalicense.com/?fullname=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica%40gmail.com%3E%20(https%3A%2F%2Fionicabizau.net)&year=2011#license-mit
[website]: https://ionicabizau.net
[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md
