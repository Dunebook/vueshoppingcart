<template>
  <div class="box">
    <div class="cart-item__details">
      <p class="is-inline">{{cartItem.title}}</p>
      <div>
        <span class="cart-item--price has-text-info has-text-weight-bold">
          ${{cartItem.price}} X {{cartItem.quantity}}
        </span>
        
        <span>
          <i class="fa fa-arrow-circle-up cart-item__modify" @click="addCartItem(cartItem)"></i>
          <i class="fa fa-arrow-circle-down cart-item__modify" @click="removeCartItem(cartItem)"></i>
        </span>
      </div>
      
    </div>
    <div class="cart-item__image">
      <img width="96" height="96" :src="require('../../assets/' + cartItem.image_tag)" />
    </div>
  </div>
</template>
<script>
import { mapActions } from 'vuex';

export default {
  name: 'CartListItem',
  props: ['cartItem'],
  methods: {
    ...mapActions([
      'addCartItem',
      'removeCartItem'
    ])
  }
}
</script>
<style scoped>
.cart-item {
  padding: 10px 0;
}

.cart-details {
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  padding: 15px;
}

.fa-arrow-circle-up, .fa-arrow-circle-down {
    margin-left: 6px;
}

.cart-item__details {
  float: right;
  /* width: 250px; */
  padding: 10px;
}

.cart-item__image img {
  float: left;
  height: 70px;
}
</style>