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
<!--    <a @click="toggleSidebar" class="top-bar-cart-link">
      <i class="icofont-cart-alt icofont-1x"></i>
      <span>Cart ({{ totalQuantity }})</span>
    </a>-->
  </header>
  <router-view/>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

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
