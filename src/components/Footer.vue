<template>
  <div class="footer">
    <div class="cart-icon">
      Cart Icon
    </div>
    <button class="add-to-cart"
      v-on:click="addToCart"
      v-hammer:press="() => addToCart">
      Add to Cart
    </button>
    
  </div>
</template>

<script>
import anime from "animejs";

export default {
  name: "Footer",
  props: {
    contents: Array
  },
  computed: {

  },
  watch: {

  },
  methods: {
    addToCart: function() {
      console.log('add to cart');
    }
  }
};
</script>

<style scoped lang="scss">
.footer {
  background-color: purple;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-around;
  padding: 1rem;

}

</style>
