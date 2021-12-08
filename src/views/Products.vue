<template>
  <div>
    <main class="wrapper">
        <h1>Products</h1>
        <div class="card-container">

          <div class="card" v-for="(item, idx) in inventory" :key="item.id">
            <div class="card-title">
              {{ item.name }}
            </div>
            <div class="card-body">
              <i class="icofont-10x icofont-{{ item.icon }}"></i>
              <form>
                <div class="row">
                  <div class="cell">
                    <label>Type:</label>
                  </div>
                  <div class="cell">
                    <em>{{ item.type }}</em>
                  </div>
                </div>
                <div class="row">
                  <div class="cell">
                    <label>Price:</label>
                  </div>
                  <div class="cell">
                    ${{ item.price.USD }}
                  </div>
                </div>
                <div class="row">
                  <div class="cell">
                    <label>Quantity:</label>
                  </div>
                  <div class="cell">
                    <input type="number" value="0">
                  </div>
                </div>
              </form>
            </div>
            <div class="card-footer">
              <button class="btn btn-light">Add to cart</button>
            </div>
          </div>

        </div>
      </main>
        <footer class="footer-class">
          vue 3
        </footer>
  </div>
</template>

<script>
import food from '../food.json'
export default {
  name: 'Products',
  components: {},
  data () {
  	return {
  		inventory: food
  	} 
  },
}
</script>
