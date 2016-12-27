# Vue.js & Nested Lists

While working on a project I stumbled on a problem with showing nested lists. I was trying to display a list of users and then on clicking a user name I wanted to display a list of their orders.

The work was really just for a demonstration and I was just using a single component to show the data.

Well, once I got to the part where I wanted to show the order data, I quickly realized what I was doing wasn't going to work. 

Download / clone this repo to find out what was wrong.

Full explanation here on my <a href="http://patrickwho.me/vue-js-nested-list-rendering/" target="_blank">Vue.js blog</a>.

## Branches

master - the broken version demonstrating the problem
fixed - the fixed version

Examine the 'master' branch and see if you can't figure out a way to fix the problem before switching to 'fixed' to see my solution.

## Build Setup

This repo uses the Vue CLI webpack-simple template

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

