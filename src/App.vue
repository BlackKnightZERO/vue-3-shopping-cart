<template>

  <header class="top-bar spread">
      <nav class="top-bar-nav">
        <router-link to="/" class="top-bar-link">
          <i class="icofont-spoon-and-fork"></i>
          <span>Home</span>
        </router-link>
        <router-link to="/products" class="top-bar-link">
          <span>Products</span>
        </router-link>
        <router-link to="past-orders" class="top-bar-link">
          <span>Past Orders</span>
        </router-link>
      </nav>
      
      <div to="#" class="top-bar-cart-link" @click="toggleSideBarCart">
        <i class="icofont-cart-alt icofont-1x"></i>
        <span id="nav-cart-item-count">Cart ({{ cartItemCount }})</span>
      </div>
      
  </header>
  <router-view :inventory="inventory" />
  <SideBar
    v-if="isSideBarCartVisible" 
    :toggle="toggleSideBarCart"
    :cart="cart"
    :inventory="inventory"
    :remove="removeCartItem" />
</template>

<script>
import SideBar from '@/components/SideBar.vue'
import food from '@/food.json'


export default {
  components: {
    SideBar
  },
  data() {
    return {
      isSideBarCartVisible: false,
      totalCartItemType:0,
      inventory: food,
      cart:{},
    }
  },
  computed:{
    cartItemCount:{
      get() {
        return Object.values(this.cart).reduce((acc,curr,index) => {
          return acc + curr
        }, 0)
      }
    }
  },
  methods: {
    addToCart(name, idx) {
        if( !this.cart[name] ) this.cart[name] = 0
        this.cart[name] += this.inventory[idx].quantity
        this.inventory[idx].quantity = 0
        console.log(this.cart)
      },
      toggleSideBarCart(){
        this.isSideBarCartVisible = !this.isSideBarCartVisible
      },
      removeCartItem(name) {
        delete this.cart[name]
      }
  },
}
</script>

