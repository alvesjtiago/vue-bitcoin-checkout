![Demo](https://user-images.githubusercontent.com/407470/47375163-8dd2ec00-d6e7-11e8-99ab-0b1381f404c6.gif)

# Vue.js Bitcoin Checkout page

If you sell digital products online and you're looking for an easy way to accept bitcoin this is a demo project that allows you to specify the address and amount you'd like to receive to automatically access your content. Think of it as an alternative to Gumroad or Stripe checkout button for crypto.

It is built with Vue.js and the main component is `Checkout.vue` where QR code rendering, socket connections and callbacks are handled.
It connects to Bitpay's servers to access real-time information about payments.

Demo site - [https://checkout-demo.tiagoalves.me/](https://checkout-demo.tiagoalves.me/)

*(This is a work in progress. Use at your own risk in production.)*

## One-click deployment

<!-- Markdown snippet -->
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/alvesjtiago/vue-bitcoin-checkout)

## Environment variables

* `VUE_APP_BITCOIN_NETWORK`: Set to test or mainnet
* `VUE_APP_BITCOIN_ADDRESS`: The bitcoin address where you want to get paid
* `VUE_APP_CONTENT_URL`: The url of the content you want to give access to after paying
* `VUE_APP_BITCOIN_AMOUNT`: The amount in bitcoin you want to charge

## Development

### Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn run serve
```

### Compiles and minifies for production
```
yarn run build
```

### Lints and fixes files
```
yarn run lint
```
