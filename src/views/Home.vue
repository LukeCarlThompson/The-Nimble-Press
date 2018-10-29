<template>
  <div class="home">
    <ShopMain />
  </div>
</template>

<script>
// @ is an alias to /src
import ShopMain from "@/components/ShopMain.vue";

export default {
  name: "Home",
  components: {
    ShopMain
  }
};
</script>
