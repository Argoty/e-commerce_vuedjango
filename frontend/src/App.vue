<template>
  <div class="wrapper">
    <nav class="navbar is-dark">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item"
          ><strong>E-commerce</strong></router-link
        >

        <a
          class="navbar-burger"
          aria-label="menu"
          aria-expanded="false"
          data-target="navbar-menu"
          @click="showMobileMenu = !showMobileMenu"
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div class="navbar-menu" id="navbar-menu" :class="{'is-active': showMobileMenu}">
        <div class="navbar-end">
          <router-link to="/summer" class="navbar-item">Summer</router-link>
          <router-link to="/winter" class="navbar-item">Winter</router-link>

          <div class="navbar-item">
            <div class="buttons">
              <router-link to="/log-in" class="button is-light"
                >Log in</router-link
              >
              <router-link to="/cart" class="button is-success">
                <span class="icon">
                  <i class="fas fa-shopping-cart"></i>
                </span>
                <span>Cart ({{ cartTotalLenght }})</span>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <section class="section">
      <router-view />
    </section>
    
    <footer class="footer">
      <p class="has-text-centered">Copyright (c) 2022 by Javier Argoty</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      showMobileMenu: false,
      cart: {
        items: [

        ]
      }
    }
  },

  beforeCreate() {
    this.$store.commit("initializeStore");
  },
  mounted() {
    this.cart = this.$store.state.cart;
  },
  computed: {
    cartTotalLenght() {
      let totalLenght = 0;
      this.cart.items.forEach(i => totalLenght += i.quantity);
      return totalLenght;
    }
  }
}
</script>

<style lang="scss">
@import "../node_modules/bulma";
</style>
