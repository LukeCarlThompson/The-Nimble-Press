<template>
  <div class="extra-ingredients-wrap">
    <h1>Extras</h1>
    <!-- <select class="extras-chooser-list" v-on:change="selectedIngredientsList" value="fruit">
      <option v-for="(ingredient, key) in ingredients"
        :key="key"
        :value="key">
        {{ key }}
      </option>
    </select> -->
    <div class="ingredients-swiper-wrap">
      <Ingredient
        v-for="(fruit, i) in ingredients.fruit"
        :bottle-position="bottlePosition(i)"
        :ingredient="ingredients.fruit[i]"
        :key="fruit.name"
        @pannedRight="decrementCounter"
        @pannedLeft="incrementCounter"/>
    </div>
    <div>
      <button 
        class="add-ingredient btn" 
        @click="addHandler">Add</button>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import Ingredient from "@/components/Ingredient.vue";

export default {
  name: "ExtraIngredients",
  components: {
    Ingredient
  },
  props: {
    ingredients: Object,
    selectedJuice: Object
  },
  data: function() {
    return {
      counter: 3,
      classes: [
        "off-screen-right",
        "far-right",
        "right",
        "selected",
        "left",
        "far-left",
        "off-screen-left"
      ]
    };
  },
  computed: {
    // selectedIngredientsList: function() {
    //   let ingredientsType = document.querySelector('.extras-chooser-list').value;
    //   // console.log('this.ingredients[ingredientsType]', this.ingredients[ingredientsType])
    //   return this.ingredients[ingredientsType];
    // },
  },
  methods: {
    selectedIngredientsList: function() {
      let ingredientsType = document.querySelector(".extras-chooser-list")
        .value;

      console.log(
        "this.ingredients[ingredientsType]",
        this.ingredients[ingredientsType]
      );

      return this.ingredients[ingredientsType];
    },
    incrementCounter: function() {
      // this check stops the first bottle from being swiped past the center position
      if (this.counter >= this.classes.length - 4) {
        // console.log("increment limit reached");
        return;
      } else {
        this.counter += 1;
      }
    },
    decrementCounter: function(item) {
      // This check stops the last bottle from being swiped past the center position
      if (this.counter <= -(this.ingredients.fruit.length - 4)) {
        // console.log("decrement limit reached");
        return;
      } else {
        this.counter -= 1;
      }
    },
    bottlePosition: function(i) {
      // set the class index equal to the counter plus the bottles index from the v-for loop
      let classIndex = this.counter + i;

      // If the counter goes below zero make it 0 (apply first class in classes array)
      if (this.counter + i <= 0) {
        classIndex = 0;
      }
      // If the counter goes higher than the length of the array
      // Set it to be one less than the array.length
      // (sets classIndex to choose the last class in the array)
      if (this.counter + i >= this.classes.length) {
        classIndex = this.classes.length - 1;
      }

      // if classIndex puts bottle in the middle then it's selected value to true and all the rest to false
      // the selected juice gets sent to the juiceInfoCard component
      if (this.classes[classIndex] == "selected") {
        this.ingredients.fruit[i].selected = true;
        this.selectedIngredient = this.ingredients.fruit;
      } else {
        this.ingredients.fruit[i].selected = false;
      }

      // return the appropriate class from the classes array
      return this.classes[classIndex];
    },
    addHandler: function() {
      // filter through the ingredients to find the one that is selected
      let selectedIngredient = this.ingredients.fruit.filter(
        fruit => fruit.selected == true
      );
      // filter creates an array, so $emit the first value of the new array up to the parent component
      this.$emit("addIngredient", selectedIngredient[0]);
    }
  }
};
</script>

<style scoped lang="scss">
.extra-ingredients-wrap {
  position: relative;
}

.extras-chooser-list {
  list-style: none;
  margin: 1rem;
  padding-left: 0;
  li {
    font-size: 1.5rem;
    margin: 1rem 0;
  }
}

.ingredients-swiper-wrap {
  position: relative;
  height: 280px;
}

.ingredient {
  width: 20%;
  display: block;
  position: absolute;
  transition: transform 0.5s cubic-bezier(0.5, 0.5, 0, 0.7);
  transform-origin: 50% 20%;
  top: 10px;
  right: 0;
}

.add-ingredient {
}

.off-screen-left {
  transform: translateX(-500%) scale(0.3) rotate(15deg);
}
.far-left {
  transform: translateX(-400%) scale(0.4) rotate(0);
}
.left {
  transform: translateX(-320%) scale(0.6) rotate(0);
}
.selected {
  transform: translateX(-200%) scale(1) rotate(0);
}
.right {
  transform: translateX(-80%) scale(0.6) rotate(0);
}
.far-right {
  transform: translateX(0) scale(0.4) rotate(0);
}
.off-screen-right {
  transform: translateX(100%) scale(0.3) rotate(-15deg);
}
</style>
