<template>
  <div class="hello">
    <Checkout 
      network="test" 
      address="mvnuXPHJz5kRbD5vEDeqfmoQpY9Hezbuer"
      :amount=0.001
      @completedPayment="completedPayment"
      v-if="showCheckout"
    />
    <div v-html="message"></div>
  </div>
</template>

<script>
import Checkout from './Checkout'
export default {
  name: 'Home',
  data: function() {
    return {
      message: "",
      showCheckout: true
    }
  },
  components: {
    Checkout
  },
  methods: {
    completedPayment() {
      this.showCheckout = false
      this.message = `Thank you for your payment. <a href="https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf" target="_blank">Here's the download link.</a>`
    }
  }
}
</script>