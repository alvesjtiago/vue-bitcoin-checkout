![Demo](https://user-images.githubusercontent.com/407470/47375163-8dd2ec00-d6e7-11e8-99ab-0b1381f404c6.gif)

# Checkout Bitcoin demo

If you sell digital products online and you're looking for an easy way to accept bitcoin this is a demo project that allows you to specify the address and amount you'd like to receive to automatically access your content. Think of it as an alternative to Gumroad or Stripe checkout button for crypto.

It is built with Vue.js and the main component is `Checkout.vue` where QR code rendering, socket connections and callbacks are handled.
It connects to Bitpay's servers to access real-time information about payments. Change the `network` prop to connect to test or mainnet.

Demo site - [https://checkout-demo.tiagoalves.me/](https://checkout-demo.tiagoalves.me/)

*(This is a work in progress. Use at your own risk in production.)*

## One-click deployment

<!-- Markdown snippet -->
[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/alvesjtiago/checkout-demo)

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
