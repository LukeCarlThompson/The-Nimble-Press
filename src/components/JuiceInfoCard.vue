<template>
  <div class="juice-info-card" >
    <transition name="slide-fade" mode="out-in">
      <div class="juice-info" :key="juiceInfo.name">
        <h1 class="juice-title">{{ juiceInfo.name }}</h1>
        <div class="size-chooser">
          <div class="size-chooser-text-wrap">
            <h4>Choose Size</h4>
            <span>Medium 350ml</span>
            <span class="price">$4.95</span>
          </div>
        </div>
        <ul>
          <li class="juice-ingredient" v-for="(juice, i) in juiceInfo.ingredients" :key="i">
            {{ juice }}
          </li>
        </ul>
      </div>

    </transition>


<!-- <transition name="slide-fade" mode="out-in">
  <div :key="value">
    {{ value }}
  </div>
</transition> -->
    <!-- {{juiceColor.top}}
    {{juiceColor.bottom}}
    <button :style="{ backgroundColor: juiceColor.bottom }"></button> -->

  </div>

</template>

<script>
export default {
  name: "JuiceInfoCard",
  // data() {
  //   return {
  //     juiceColor: {
  //       top: "#F6D663",
  //       bottom: "#F77C1C"
  //     }
  //   };
  // },
  props: {
    juiceInfo: Object
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.juice-info-card {
  background-color: pink;
  margin-top: 200px;
  height: 600px;
  width: 100%;
  h1 {
    padding-top: 60px;
  }
  ul {
    padding: 0;
    text-align: left;
    max-width: 300px;
    margin: 20px auto;
  }
}
.juice-title {
  
}

.size-chooser {
  border: 1px solid red;

}
.size-chooser-text-wrap {
  display: flex;
  h4 {
    margin: 0 10px;
  }
}

.juice-ingredient {
  list-style: none;
  font-weight: 600;
}

.slide-fade-enter-active {
  transition: all 1s cubic-bezier(0, 1, 0, 1);
}
.slide-fade-leave-active {
  transition: all .2s linear;
}
.slide-fade-enter {
  transform: translateY(20%) scaleY(1.1) scaleX(0.9);
  transform-origin: bottom;
  opacity: 0;
}
.slide-fade-leave-to {
  opacity: 0;
}
</style>