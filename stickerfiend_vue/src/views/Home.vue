<template>

  <div class="home">
 <section class ="hero is-small is-dark mb-4"> 
  <div class = "hero-body has-text-centered">
    <p class="title mb-6">
      Welcome to StickerFiend
    </p>
    <p class ="subtitle">
       - The Best Online Sticker Store for Computer Programmers and Developers - 
    </p>
    
  </div>
  </section>

  <div class="columns is-multiline">
    <div class ="column is-12">
      <h2 class="is-size-2 has-text-centered " style="color:white;">Latest Stickers</h2>
    </div>
     
      <ProductBox
        v-for="product in latestProducts"
        v-bind:key="product.id"
        v-bind:product="product" />
      </div>
    </div>
  

</template>

<script>
import axios from 'axios'
 
import ProductBox from '@/components/ProductBox'

export default {
  name: 'Home',
  data() {
    return{
      latestProducts: []
    }
  },
  components: { 
    ProductBox,
  },
  mounted(){
    this.getLatestProducts()
    document.title = "Home | Stickerfiend"
  },
  methods:{
    getLatestProducts(){
     axios
        .get('/api/v1/latest-products/')
        .then(response => {
          this.latestProducts = response.data
      })
        .catch(error => {
          console.log(error)
      })
    }
  }
}
</script>

