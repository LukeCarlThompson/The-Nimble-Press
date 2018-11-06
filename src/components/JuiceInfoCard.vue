<template>
  <div class="juice-info-card" >
    <transition
      name="slide-fade" 
      mode="out-in">
      <div 
        :key="juiceInfo.name" 
        class="juice-info">
        <h1 class="juice-title">{{ juiceInfo.name }}</h1>
        <span class="price">{{this.price}}</span>
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
          <transition-group name="ingredients-list">
            <div class="juice-ingredient-wrap"
              v-for="(juice, i) in juiceInfo.ingredients" 
              :key="juice" >
              <li class="juice-ingredient">
                {{ juice }}
                <span class="remove-icon"
                  v-on:click="removeIngredient(i)"
                  v-hammer:press="() => removeIngredient(i)">
                </span>
              </li>
            </div>
          </transition-group>
        </ul>
      </div>

    </transition>

  </div>

</template>

<script>
export default {
  name: "JuiceInfoCard",
  props: {
    juiceInfo: Object
  },
  computed: {
    price: function() {
      let thePrice;
      console.log(this.juiceInfo.size);
      if(this.juiceInfo.size == 2) {
        thePrice = '$5.95';
      } else if(this.juiceInfo.size == 1) {
        thePrice = '$4.95';
      } else if(this.juiceInfo.size == 0) {
        thePrice = '$3.45';
      }
      return thePrice;
    }
  },
  methods: {
    changeBottleSize: function() {
      // this sends the event back up to the parent component so we can send it down to the bottle
      this.$emit("changeBottleSize", this.juiceInfo.size);
    },
    removeIngredient: function(i) {
      this.juiceInfo.ingredients.splice(i, 1);
      // this.delete(this.juiceInfo.ingredients, i);

    }
  }
};
</script>

<style scoped lang="scss">
.juice-info-card {
  box-shadow: 0 10px 40px rgba(10, 25, 105, 0.2),
    0 5px 20px rgba(10, 25, 105, 0.1);
  background-color: white;
  border-radius: 10px;
  padding: 10px;
  margin: 180px auto 40px;
  max-width: 400px;
  width: 100%;
  // height: 35rem;
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
      background-color: #50dbbb;
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
  display: flex;
  align-items: center;
}

.remove-icon {
  height: 25px;
  width: 25px;
  background-color: rgb(197, 84, 84);
  border-radius: 100%;
  margin-left: auto;
  display: inline-block;
  position: relative;
  cursor: pointer;
  &:after {
    content: "";
    display: block;
    width: 15px;
    height: 3px;
    border-radius: 10px;
    background-color: white;
    position: absolute;
    top: 11px;
    left: 5px;
  }
}

.ingredients-list-enter-active, .ingredients-list-leave-active {
  transition: all 0.2s ease-in;
  // position: absolute;
}
.ingredients-list-enter, .ingredients-list-leave-to {
  transform: translateX(-20%);
  opacity: 0;
}
.ingredients-list-move {
  transition: transform 0.6s ease-in-out 0.1s;
}
.ingredients-list-leave-active {
  position: absolute;
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
