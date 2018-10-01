<template>
  <div class="home">
    <bottleSwiper />
  </div>
</template>

<script>
// @ is an alias to /src
import bottleSwiper from "@/components/BottleSwiper.vue";

export default {
  name: "Home",
  components: {
    bottleSwiper
  }
};
</script>
