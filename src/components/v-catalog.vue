<template>
    <div class="v-catalog">
        <router-link :to="{name: 'cart', params: {cart_data: CART}}">
            <div class="v-catalog__link_to_cart">Cart: {{ CART.length }}</div>
        </router-link>

        <div class="v-catalog__list">
            <v-catalog-item
                v-for="product in PRODUCTS"
                :key ="product.article"
                :product_data="product"
                @addToCart="addToCart"
            />
        </div>
    </div>
</template>

<script>
    import vCatalogItem from './v-catalog-item'
    import {mapActions, mapGetters} from 'vuex'

    export default {
        name: "v-catalog",
        components: {
            vCatalogItem,
        },
        props: {

        },
        computed: {
            ...mapGetters([ //чтобы не тянуть путь из store
                'PRODUCTS',
                'CART'
            ])
        },
        methods:{
            ...mapActions([
                'GET_PRODUCTS_FROM_API', //чтобы не тянуть путь из store
                'ADD_TO_CART'
            ]),
            addToCart(data) {
                this.ADD_TO_CART(data)
            },
        },
        data(){
            return{

        }
        },
        mounted() {
            this.GET_PRODUCTS_FROM_API()
                .then((response) =>{
                    if (response.data) {
                        console.log('Data arrive')
                    }
                })
            }
        }
</script>

<style lang="scss">
    .v-catalog{
        &__list{
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
        }
        &__link_to_cart{
            position: absolute;
            top: 10px;
            right: 10px;
            padding: $padding*2;
            border: 1px solid #999;
        }
    }
</style>