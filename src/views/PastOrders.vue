<template>
  <div>
    <main class="wrapper">
        <h1>Past Orders</h1>

        <table class="product-table">
          <thead>
            <tr>
              <td><span class="sr-only">Product Image</span></td>
              <td>Product</td>
              <td>Price</td>
              <td>Quantity</td>
              <td>Total</td>
              <td><span class="sr-only">Actions</span></td>
            </tr>
          </thead>
          <tbody>

            <tr v-for="(key, value) in cart" :key="key">
              <td><i class="icofont-carrot icofont-4x"></i></td>
              <td>{{ value }}</td>
              <td>${{ getPrice(value) }}</td>
              <td>{{ key }}</td>
              <td>${{ (getPrice(value) * key).toFixed(2) }}</td>
              <td><button class="btn btn-dark">Ordered</button></td>
            </tr>
          </tbody>
        </table>
      </main>
  </div>
</template>

<script>
export default {
  props: ['cart', 'inventory'],
  methods: {
    getPrice(name){
        const productName = this.inventory.find((p) => {
          return p.name === name
        })

        return productName.price.USD
        // console.log(name);
        // return 0;
      },
  },
  mounted(){
    // console.log(this.inventory);
  }
}
</script>
