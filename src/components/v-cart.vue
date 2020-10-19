<template>
    <div class="v-cart">
        <router-link :to="{name: 'catalog'}">
            <div class="v-catalog__link_to_cart">Вернуться в каталог</div>
        </router-link>
        <h1>Cart</h1>
        <p v-if="!cart_data.lenght">Корзина пустая...</p>
        <v-cart-item
                v-for="(item, index) in cart_data"
                :key ="item.article"
                :cart_item_data="item"
                @deleteFromCart="deleteFromCart(index)"
        />
        <div class="v-cart__total">
            <p class="total__name">Total: </p>
            <p>{{ cartTotalCost }}</p>
        </div>
    </div>
</template>

<script>
    import vCartItem from './v-cart-item'
    import {mapActions} from 'vuex'

    export default {
        name: "v-cart",
        components: {
            vCartItem
        },
        props: {
            cart_data: {
                type: Object,
                default(){
                    return{}
                }
            }
        },
        computed: {
            // cartTotalCost(){
            //     let result = []
            //
            //     for (let item of this.cart_data){
            //         result.push(item.price * item.quantity)
            //     }
            //
            //     result = result.reduce(function (sum, el) {
            //         return sum*el
            //     });
            //     return result
            // }
        },
        methods: {
            ...mapActions([
                'DELETE_FROM_CART'
            ]),
            deleteFromCart(index){
                console.log(this.DELETE_FROM_CART(index))
                // this.DELETE_FROM_CART(index)
            },
        }
    }
</script>

<style lang="scss">

    .v-cart{
        &__total{
            position: fixed;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100%;
            color: #fff;
            font-size: 30px;
        }
        .total__name{
            padding: $padding*3;
            background: green;
        }
    }

</style>