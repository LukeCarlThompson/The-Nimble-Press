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
          <input type="range" id="size" name="size" min="0" max="2" />
        </div>
        <ul>
          <li class="juice-ingredient" v-for="(juice, i) in juiceInfo.ingredients" :key="i">
            {{ juice }}
          </li>
        </ul>
      </div>

    </transition>

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
  box-shadow: 0 10px 40px rgba(51, 66, 150, 0.2);
  background-color: white;
  border-radius: 10px;
  padding: 10px;
  margin: 160px auto 40px;
  height: 600px;
  max-width: 400px;
  width: 100%;
  h1 {
    padding-top: 40px;
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
  input {
    width: 80%;
    margin: 20px;
  }
}
.size-chooser-text-wrap {
  display: flex;
  h4 {
    font-size: 1.4rem;
    margin: 0 auto 0 0;
    flex: 1 0 50%;
  }
  span {
    flex: 1 1 auto;
  }
  .price {
    font-size: 2rem;
    font-weight: 600;
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