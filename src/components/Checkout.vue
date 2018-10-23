<template>
  <div class="hello">
    <VueQrcode class="mt4" :value="qrcodeAddress" :options="{ size: 250 }"></VueQrcode>
    <div class="f7 fw1 lh-copy">{{ address }}</div>
    <div class="mt4">{{ message }}</div>
  </div>
</template>

<script>
import VueQrcode from '@xkeshi/vue-qrcode'
const io = require('socket.io-client')

const eventToListenTo = 'tx'
const room = 'inv'

export default {
  name: 'Checkout',
  props: {
    network: String,
    address: String,
    amount: Number,
  },
  data: function() {
    return  {
      qrcodeAddress: '',
      message: ""
    }
  },
  beforeMount(){
    this.qrcodeAddress = `bitcoin:${this.address}`
    const socket = this.network == "test" ? io("https://test-insight.bitpay.com/") : io("https://insight.bitpay.com/")

    const ref = this

    socket.on('connect', function() {
      // Join the room.
      socket.emit('subscribe', room)
      ref.message = `Waiting for ${ref.amount} BTC payment...`
    })

    socket.on(eventToListenTo, function(data) {
      if (data.vout.some(e => Object.keys(e)[0] === ref.address)) {
        if (data.vout.some(e => e[ref.address] / 100000000 === ref.amount)) {
          ref.message = ""
          ref.$emit('completedPayment')
        }
      }
    })
  },
  components: {
    VueQrcode
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
