<template>  

 <div class ="column is-3 " style="border-radius:5px;" >
        <div class="box" style="background-color:#989C94;">
          <figure class="image mb-4 is-4" >
            <img style="border-top-left-radius:5px;border-top-right-radius:5px;" :src="product.get_thumbnail">
            </figure>

              <h3 class ="is-size-6 has-text-white">{{ product.name }}</h3>
              <p class ="is-size-6 has-text-white">Price: ${{ product.price }}</p>
               <router-link v-bind:to="product.get_absolute_url" class = "button is-success mt-2">View Details</router-link>
          </div>
      </div>

</template>

<script>
export default {
    name: 'ProductBox',
    props:{
        product: Object
    }
}
</script>

<style scoped>
.image {
  margin-top: -1.25rem;
  margin-left: -1.25rem;
  margin-right: -1.25rem;

}
</style>