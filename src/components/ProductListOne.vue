<template>
  <div id="product-list-one">
    <h2>Product List One</h2>
    <ul>
      <li v-for="(product, idx) in saleProducts" :key="idx">
        <span class="name">{{ product.name }}</span>
        <span class="price">£{{ product.price }}</span>
      </li>
    </ul>
    <button @click.prevent="reducePrice(4)">Reduce Price</button>
  </div>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
  computed: {
    products() {
      return this.$store.state.products;
    },
    // saleProducts() {
    //   return this.$store.getters.saleProducts;
    // },
    ...mapGetters(["saleProducts"]),
  },
  methods: {
    // reducPrice: function (amount) {
    // //   this.$store.commit("reducePrice");
    //     this.$store.dispatch('reducePrice', amount)
    // },
    ...mapActions(["reducePrice"]),
  },
};
</script>

<style>
#product-list-one {
  background: #fff8b1;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.2);
  margin-bottom: 30px;
  padding: 10px 20px;
}
#product-list-one ul {
  padding: 0;
}
#product-list-one li {
  display: inline-block;
  margin-right: 10px;
  margin-top: 10px;
  padding: 20px;
  background: rgba(255, 255, 255, 0.7);
}
.price {
  font-weight: bold;
  color: #e8800c;
}
</style>