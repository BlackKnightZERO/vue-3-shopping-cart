<template>
  <div>
    <main class="wrapper">
        <h1>Products</h1>
        <div class="card-container">

          <ProductCard
            v-for="(product,idx) in inventory" 
            :key="product.id"
            :product="product"
            :idx="idx"
            :addtocart="addtocart"
          />

        </div>
      </main>
        <footer class="footer-class">
          vue 3
        </footer>
  </div>
</template>

<script>
import ProductCard from '@/components/ProductCard'
export default {
  name: 'Products',
  components: {
    ProductCard
  },
  props: ['product', 'addtocart', 'idx', 'inventory'],
}
</script>
