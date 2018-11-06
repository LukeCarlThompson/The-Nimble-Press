<template>
  <div class="cart-wrap">
    <h1>Cart</h1>
    <h2 v-if="!cartHasItems">Your cart is currenly Empty</h2>
    <div 
      v-if="cartHasItems" 
      class="cart-list-wrap">
      <h2>Your Items</h2>
      <ul>
        <li
          v-for="(item, i) in this.cartContents"
          :key="item.name + i">
          {{ item.name }}
          <span class="price">{{ price(item.size) }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: {
    // cartContents: ['default 01', 'default 02']
  },
  computed: {
    cartContents: function() {
      return this.$route.params.cartContents;
    },
    cartHasItems: function() {
      return this.cartContents;
    }
  },
  watch: {},
  methods: {
    price: function(size) {
      let thePrice;
      console.log(size);
      if (size == 2) {
        thePrice = "$5.95";
      } else if (size == 1) {
        thePrice = "$4.95";
      } else if (size == 0) {
        thePrice = "$3.45";
      }
      return thePrice;
    }
  }
};
</script>

<style scoped lang="scss">
.cart-wrap {
  box-shadow: 0 10px 40px rgba(10, 25, 105, 0.2),
    0 5px 20px rgba(10, 25, 105, 0.1);
  background-color: white;
  border-radius: 10px;
  padding: 10px;
  margin: 40px auto 40px;
  max-width: 400px;
  width: 100%;
  ul {
    padding: 0;
    text-align: left;
    margin: 20px auto;
    li {
      list-style: none;
      margin: 20px 0;
      padding-bottom: 10px;
      border-bottom: 1px solid rgb(204, 204, 204);
    }
  }
}
.price {
  font-weight: 600;
  font-size: 20px;
  float: right;
  color: rgb(87, 87, 87);
}
</style>
