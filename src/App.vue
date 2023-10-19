<template>
  <header class="top-bar spread">
    <nav class="top-bar-nav">
      <router-link to="/" class="top-bar-link nav-item">
          <i class="icofont-spoon-and-fork"></i>
          <span>Home</span>
      </router-link>
      <router-link to="/products" class="top-bar-link nav-item">
          <span>Products</span>
      </router-link>
      <router-link to="/orders" class="top-bar-link nav-item">
          <span>Past Orders</span>
      </router-link>
    </nav>
   <div @click="toggleSidebar" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ totalQuantity }})</span>
    </div>
  </header>
  <router-view :inventory="inventory"/>

  <the-sidebar
    v-if="showSidebar"
    :toggle="toggleSidebar"
    :cart="cart"
    :inventory="inventory"
    :remove="removeItem"
  />
</template>

<script>
import food from './assets/food.json'
import TheSidebar from './components/TheSidebar.vue'

export default {
  data () {
    return {
      showSidebar: false,
      inventory: food,
      cart: {}
    }
  },

  components: {
    TheSidebar
  },

  computed: {
    totalQuantity () {
      return Object.values(this.cart).reduce((sum, curr) => {
        return sum + curr
      }, 0)
    }
  },

  methods: {
    addToCart (name, index) {
      if (!this.cart[name]) this.cart[name] = 0
      this.cart[name] += this.inventory[index].quantity
      this.inventory[index].quantity = 0
      console.log('*********cart: ', this.cart)
    },
    toggleSidebar () {
      this.showSidebar = !this.showSidebar
    },
    removeItem (name) {
      delete this.cart[name]
    }
  }
}
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  // padding: 30px;
  .nav-item {
    font-weight: bold;
    color: #2c3e50;
    padding-right: 9px;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
