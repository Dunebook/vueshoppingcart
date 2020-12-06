
<template>
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <a class="navbar-item" href="https://bulma.io">
          <img
            src="https://bulma.io/images/bulma-logo.png"
            width="112"
            height="28"
          />
        </a>
        <a
          role="button"
          class="navbar-burger burger"
          aria-label="menu"
          aria-expanded="false"
          data-target="navbarBasicExample"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>
      <div id="navbarBasicExample" class="navbar-menu">
        <div class="navbar-end">
          <div class="navbar-item">
            <div class="buttons">
              <router-link to="/inventory" class="button is-info">
               <strong> Inventory</strong>
              </router-link>
              <router-link to="/cart"  class="button is-light">
                <i class="fa fa-shopping-cart"></i> <span>{{cartQuantity}}</span>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </nav>
</template>
<script>
import {mapGetters} from "vuex"
export default {
    name: "Navbar",
    computed: {
    ...mapGetters([
      'cartQuantity'
    ])
  },
  created() {
    this.$store.dispatch("getCartItems");
  }
}
</script>