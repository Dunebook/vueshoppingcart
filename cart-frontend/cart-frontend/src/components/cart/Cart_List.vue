<template>
  <div id="cart">
    <div class="cart--header has-text-centered">
      <i class="fa fa-2x fa-shopping-cart"></i>
    </div>
    <p v-if="!cartItems.length" class="cart-empty-text has-text-centered">
      Add some items to the cart!
    </p>
    <ul>
      <li class="cart-item" v-for="cartItem in cartItems" :key="cartItem.id">
          <CartListItem :cartItem="cartItem"/>
      </li>
      <div class="cart-details">
        <p>
          Total Quantity:
          <span class="has-text-weight-bold">{{ cartQuantity }}</span>
        </p>
        <p class="cart-remove-all--text" @click="removeAllCartItems">
          <i class="fa fa-trash"></i>Remove all
        </p>
      </div>
    </ul>
    <button :disabled="!cartItems.length" class="button is-info">
      Checkout (<span class="has-text-weight-bold">${{ cartTotal }}</span>)
    </button>
  </div>
</template>
<script>
import { mapGetters, mapActions } from "vuex";
import CartListItem from "./Cart_List_Item";
export default {
  name: "CartList",
  computed: {
    ...mapGetters(["cartItems", "cartTotal", "cartQuantity"]),
  },
  created() {
    this.$store.dispatch("getCartItems");
  },
  methods: {
    ...mapActions(["removeAllCartItems"]),
  },
  components: {
    CartListItem
  },
};
</script>
<style scoped>
#cart {
  height: 100%;
  padding: 30px 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
}

.cart-empty-text {
  padding: 10px 0;
}

.cart--header {
  border-bottom: 1px solid #e8e8e8;
  padding-bottom: 15px;
}

.cart-item {
  padding: 10px 0;
}

.cart-details {
  font-size: 12px;
  display: flex;
  justify-content: space-between;
  padding: 15px;
}

.cart-remove-all--text {
  cursor: pointer;
}

.cart-remove-all--text .fa {
  padding-right: 5px;
}

ul {
  width: 60%;
}

.button {
  width: 60%;
}

.box {
  height: 90px;
  padding: 10px;
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

.cart-item__modify {
  cursor: pointer;
  margin: 0 1px;
}
</style>
