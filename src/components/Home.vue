<template>
  <div class="hello">
    <section class="flex-ns vh-100 items-center">
      <div class="mw7 ph5">
        <img :src="imageUrl"> 
      </div>
      <div class="tc tl-ns ph3">
        <h1 class="f3 f1-l fw2 mb3 mt4 mt0-ns">{{title}}</h1>
        <h2 class="f5 f3-l fw1 mb4 lh-title">{{subtitle}}</h2>
        <a class="f3 link dim br1 ph4 pv3 mb2 dib white bg-dark-green" href="#" @click="showModal = true">Buy now with Bitcoin</a>
      </div>
    </section>

    <Modal v-if="showModal" @close="showModal = false"></Modal>
  </div>
</template>

<script>
import Modal from './Modal'
import image from '../assets/book.png'

export default {
  name: 'Home',
  data: function() {
    return {
      message: "",
      showCheckout: true,
      showModal: false,
      title: process.env.VUE_APP_TITLE || "Learn how to promote your product.",
      subtitle: process.env.VUE_APP_SUBTITLE || "The only resource you need to master content marketing.",
      imageUrl: process.env.VUE_APP_IMAGE_URL || image,
    }
  },
  components: {
    Modal
  }
}
</script>