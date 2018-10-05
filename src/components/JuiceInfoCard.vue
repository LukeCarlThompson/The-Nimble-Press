<template>
  <div class="juice-info-card" >
    <transition 
      name="slide-fade" 
      mode="out-in">
      <div 
        :key="juiceInfo.name" 
        class="juice-info">
        <h1 class="juice-title">{{ juiceInfo.name }}</h1>
        <span class="price">$4.95</span>
        <div class="size-chooser">
          <form id="size-form">
            <input type="radio" name="small size" id="small-size" value="0" v-model="juiceInfo.size" v-on:input="changeBottleSize" />
            <label for="small-size">Sml<br><span>275ml</span></label>
            <input type="radio" name="medium size" id="medium-size" value="1" v-model="juiceInfo.size" v-on:input="changeBottleSize" />
            <label for="medium-size">Med<br><span>350ml</span></label>
            <input type="radio" name="large size" id="large-size" value="2" v-model="juiceInfo.size" v-on:input="changeBottleSize" />
            <label for="large-size">Lrg<br><span>500ml</span></label>
          </form>
        </div>
        <ul>
          <div class="juice-ingredient-wrap"
            v-for="(juice, i) in juiceInfo.ingredients" 
            :key="i" >
            <li class="juice-ingredient">
              {{ juice }}
            </li>
          </div>
        </ul>
      </div>

    </transition>

  </div>

</template>

<script>
export default {
  name: "JuiceInfoCard",
  // data: function() {
  //   return {
  //     rangeValue: 2
  //   }
  // },
  props: {
    juiceInfo: Object
  },
  methods: {
    changeBottleSize: function() {
      // this sends the event back up to the parent component so we can send it down to the bottle
      this.$emit("changeBottleSize", this.juiceInfo.size);
    }
  }
};
</script>

<style scoped lang="scss">
.juice-info-card {
  box-shadow: 0 10px 40px rgba(10, 25, 105, 0.20), 0 5px 20px rgba(10, 25, 105, 0.1);
  background-color: white;
  border-radius: 10px;
  padding: 10px;
  margin: 180px auto 40px;
  max-width: 400px;
  width: 100%;
  @media screen and (max-width: 480px) {
    margin: 35vw auto 40px;
  }
  ul {
    padding: 0;
    text-align: left;
    max-width: 300px;
    margin: 20px auto;
  }
}

.juice-title {
  padding-top: 40px;
  font-weight: 800;
  font-size: 2.2rem;
  margin-bottom: 10px;
}

.price {
  font-size: 2.4rem;
  font-weight: 300;
  color: rgb(120, 188, 190);
}

.size-chooser {
  margin: 10px;
}

#size-form {
  display: flex;
  justify-content: space-around;
  -webkit-tap-highlight-color: transparent;
  label {
    margin: 10px 10px 10px;
    height: 75px;
    width: 75px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    border-radius: 100px;
    cursor: pointer;
    background-color: rgb(238, 245, 244);
    text-align: center;
    font-weight: 600;
    position: relative;
    z-index: 0;
    span {
      display: inline-block;
      font-size: 1.2rem;
    }
    &:before {
      content: "";
      position: absolute;
      height: 85px;
      width: 85px;
      border-radius: 100px;
      background-color: #50DBBB;
      transform: scale(0);
      opacity: 0;
      transition: transform 0.2s ease-in-out, opacity 0.1s;
      top: -5px;
      left: -5px;
      z-index: -1;
    }
  }
  input[type="radio"]:checked + label {
    color: white;
    &:before {
      transform: scale(1);
      opacity: 1;
      transition: transform 0.6s cubic-bezier(0, 0.5, 0, 1);
    }
  }
}

input[type="radio"] {
	opacity: 0;
	width: 0;
  height: 0;
  position: absolute;
}

.juice-ingredient-wrap {
  // border-top: 1px solid rgb(202, 202, 202);
  position: relative;
  padding: 15px 0;
  &:after {
    content: "";
    display: block;
    position: absolute;
    bottom: 0;
    left: 0;
    height: 1px;
    width: 100%;
    background-color: rgb(202, 202, 202);
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
  transition: all 0.2s linear;
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
