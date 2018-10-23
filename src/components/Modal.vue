<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="header">
              <a class="modal-default-button" href="#" @click="$emit('close')">
                Close
              </a>
            </slot>
          </div>
          <div class="modal-body">
            <Checkout 
              network="test" 
              address="mvnuXPHJz5kRbD5vEDeqfmoQpY9Hezbuer"
              :amount=0.001
              @completedPayment="completedPayment"
              v-if="showCheckout"
            />
            <div class="green mv6 f3" v-if="!showCheckout" v-html="message"></div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import Checkout from './Checkout'

export default {
  name: 'Modal',
  data: function() {
    return {
      message: "",
      showCheckout: true,
    }
  },
  components: {
    Checkout,
  },
  methods: {
    completedPayment() {
      this.showCheckout = false
      this.message = `Thank you for your payment.<br><a class="b green" href="https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf" target="_blank">Click here to download.</a>`
    }
  }
}
</script>

<style scoped>
  .modal-mask {
    position: fixed;
    z-index: 9998;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, .5);
    display: table;
    transition: opacity .3s ease;
  }

  .modal-wrapper {
    display: table-cell;
    vertical-align: middle;
  }

  .modal-container {
    width: 400px;
    margin: 0px auto;
    padding: 20px 30px;
    background-color: #fff;
    border-radius: 2px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
    transition: all .3s ease;
    font-family: Helvetica, Arial, sans-serif;
  }

  .modal-header h3 {
    margin-top: 0;
    color: #42b983;
  }

  .modal-body {
    margin: 20px 0;
  }

  .modal-default-button {
    color: #ddd;
    text-decoration: none;
    float: right;
  }

  /*
   * The following styles are auto-applied to elements with
   * transition="modal" when their visibility is toggled
   * by Vue.js.
   *
   * You can easily play with the modal transition by editing
   * these styles.
   */

  .modal-enter {
    opacity: 0;
  }

  .modal-leave-active {
    opacity: 0;
  }

  .modal-enter .modal-container,
  .modal-leave-active .modal-container {
    -webkit-transform: scale(1.1);
    transform: scale(1.1);
  }
</style>