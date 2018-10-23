<template>
  <div class="hello">
    <section class="flex-ns vh-100 items-center">
      <div class="mw7 ph5">
        <img src="../assets/book.png"> 
      </div>
      <div class="tc tl-ns ph3">
        <h1 class="f3 f1-l fw2 mb3 mt4 mt0-ns">Learn how to promote your product.</h1>
        <h2 class="f5 f3-l fw1 mb4 lh-title">The only resource you need to master content marketing.</h2>
        <a class="f3 link dim br1 ph4 pv3 mb2 dib white bg-dark-green" href="#" @click="showModal = true">Buy now with Bitcoin</a>
      </div>
    </section>

    <Modal v-if="showModal" @close="showModal = false"></Modal>
  </div>
</template>

<script>
import Modal from './Modal'

export default {
  name: 'Home',
  data: function() {
    return {
      message: "",
      showCheckout: true,
      showModal: false,
    }
  },
  components: {
    Modal
  }
}
</script>