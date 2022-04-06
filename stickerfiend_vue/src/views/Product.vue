<template>
    <div class = "page-product column is-10">
        <div class="columns is-multiline is-centered">
            <div class = "column is-6">
                <figure class ="image mb-6">
                    <img v-bind:src="product.get_image">
                </figure>

               
            </div>

            <div>
               
                <h2 class= "subtitle" style="color:white;margin-top:10px;">Information</h2>
                 <h1 class="title" style="color:white">{{ product.name }}</h1>
                <p style="color:#BBCDE5">Description:</p>
                
                <p style="color:white">{{ product.description }}</p>
                <p><strong style="color:white">Price: ${{ product.price}}</strong></p>
                <div class = "field has-addons mt-4">
                    <div class ="control">
                        <input type= "number" class="input" min="1" v-model="quantity">
                    </div>
                    <div class="control">
                        <a class="button is-dark" @click="addToCart" >Add to cart</a>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
import axios from 'axios'
import { toast } from 'bulma-toast'

export default {
    name:'Product',
    data(){
        return{
            product:{},
            quantity:1
        }
        
    },
    mounted() {
        this.getProduct()

    },
    methods:{
       async getProduct() {
            this.$store.commit('setIsLoading', true)

            const category_slug = this.$route.params.category_slug
            const product_slug = this.$route.params.product_slug

        await  axios
                .get(`/api/v1/products/${category_slug}/${product_slug}`)
                .then(response => {
                    this.product = response.data

                    document.title = this.product.name + ' | Stickerfiend'
                })
                .catch(error =>{
                    console.log(error)
                })
            this.$store.commit('setIsLoading', false)
        },
        addToCart() {
           
            if (isNaN(this.quantity) || this.quantity < 1) {
                this.quantity = 1
            }

            const item = {
                product: this.product,
                quantity: this.quantity
            }
            this.$store.commit('addToCart', item)
            
            toast({
               message:'the product was added to your cart',
               type: 'is-success',
               dismissable: true,
               pauseOnHover: true, 
               duration: 2000,
               position: 'bottom-right',
            })
        }

    }
}
</script>
