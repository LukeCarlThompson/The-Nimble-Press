<template>
  <div class="shop-main-wrap">
    <div class="bottle-swiper-wrap">
      <JuiceBottle
        v-for="(juice, i) in juices"
        :bottle-position="bottlePosition(i)"
        :juice="juice"
        :key="juice.name"
        @pannedRight="decrementCounter"
        @pannedLeft="incrementCounter"/>
    </div>
    <juiceInfoCard 
      :juice-info="selectedJuice"
      @changeBottleSize="changeBottleSize"/>
    <ExtraIngredients
      :selected-juice="selectedJuice"
      :ingredients="ingredients"
      @changeBottleSize="changeBottleSize"
      @addIngredient="addIngredient"/>
    <Footer
      :cartContents="cartContents"
      :selectedJuice="selectedJuice"/>
  </div>
</template>

<script>
// @ is an alias to /src
import JuiceBottle from "@/components/JuiceBottle.vue";
import JuiceInfoCard from "@/components/JuiceInfoCard.vue";
import ExtraIngredients from "@/components/ExtraIngredients.vue";
import Footer from "@/components/Footer.vue";

import anime from "animejs";

export default {
  name: "ShopMain",
  components: {
    JuiceBottle,
    JuiceInfoCard,
    ExtraIngredients,
    Footer
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
      ],
      juices: [
        {
          name: "Ginger Zinger",
          size: "2",
          selected: true,
          ingredients: ["Carrot", "Lemon", "Ginger"],
          color: {
            top: "#F6D663",
            bottom: "#F77C1C"
          }
        },
        {
          name: "Cool Kiwi",
          size: "2",
          selected: false,
          ingredients: ["Kiwi Fruit", "Kale", "Mint"],
          color: {
            top: "#B4EC51",
            bottom: "#429321"
          }
        },
        {
          name: "Tropi-Kale",
          size: "2",
          selected: false,
          ingredients: ["Kale", "Banana", "Pineapple"],
          color: {
            top: "#B4EC51",
            bottom: "#429321"
          }
        },
        {
          name: "Very Berry",
          size: "2",
          selected: false,
          ingredients: ["Kale", "Banana", "Pineapple"],
          color: {
            top: "#FDA0A8",
            bottom: "#DF0B2B"
          }
        },
        {
          name: "Grape Nectar",
          size: "2",
          selected: false,
          ingredients: ["Red Grape", "Mulberry", "Pear"],
          color: {
            top: "#A664B1",
            bottom: "#473E9D"
          }
        },
        {
          name: "Pomegranate Twist",
          size: "2",
          selected: false,
          ingredients: ["Pomegranate", "Green Apple", "Lime"],
          color: {
            top: "#A664B1",
            bottom: "#473E9D"
          }
        },
        {
          name: "Mellow Melon",
          size: "2",
          selected: false,
          ingredients: ["Watermelon", "Strawberry", "Green Apple", "Mint"],
          color: {
            top: "#FDA0A8",
            bottom: "#DF0B2B"
          }
        },
        {
          name: "Cucumber Cooler",
          size: "2",
          selected: false,
          ingredients: ["Cucumber", "Rockmelon", "Celery"],
          color: {
            top: "#B4EC51",
            bottom: "#429321"
          }
        },
        {
          name: "Boom Bap Beet",
          size: "2",
          selected: false,
          ingredients: ["Beetroot", "Strawberry", "Blueberry"],
          color: {
            top: "#FDA0A8",
            bottom: "#DF0B2B"
          }
        }
      ],
      selectedJuice: Object,
      ingredients: {
        fruit: [
          {
            name: "Strawberry",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Blueberry",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Green Apple",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Pomegranate",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Banana",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Pineapple",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Pear",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Lemon",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Orange",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Watermelon",
            color: "#DF0B2B",
            selected: false
          }
        ],
        vegetables: [
          {
            name: "Carrot",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Kale",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Cucumber",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Beetroot",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Celery",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Ginger",
            color: "#DF0B2B",
            selected: false
          },
          {
            name: "Mint",
            color: "#DF0B2B",
            selected: false
          }
        ]
      },
      cartContents: []
    };
  },
  mounted: function() {
    this.handleScroll();
  },
  methods: {
    incrementCounter: function() {
      // this check stops the first bottle from being swiped past the center position
      if (this.counter >= this.classes.length - 4) {
        // console.log("increment limit reached");
        return;
      } else {
        this.counter += 1;
      }
    },
    decrementCounter: function() {
      // This check stopes the last bottle from being swiped past the center position
      if (this.counter <= -(this.juices.length - 4)) {
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
        this.juices[i].selected = true;
        this.selectedJuice = this.juices[i];
      } else {
        this.juices[i].selected = false;
      }

      // return the appropriate class from the classes array
      return this.classes[classIndex];
    },
    changeBottleSize: function(value) {
      // loop over the juices and if it is selected then update the size value
      for (let i = 0; this.juices.length > i; i++) {
        if (this.juices[i].selected == true) {
          this.juices[i].size = value;
        }
      }
    },
    addIngredient: function(ingredient) {
      // check if the juice already has that ingredient
      const duplicateIngredient = () => {
        let isDuplicate = this.selectedJuice.ingredients.filter(
          juiceIngredient => juiceIngredient == ingredient.name
        );
        // Returns false if new ingredient does not match any ingredients in the selectedJuice ingredients array
        return isDuplicate.length > 0;
      };

      const maxIngredientsReached = () =>
        this.selectedJuice.ingredients.length >= 6;

      if (maxIngredientsReached()) {
        alert("Maximum number of ingredients reached");
      } else if (duplicateIngredient()) {
        alert("Juice already has this ingredient");
      } else {
        this.selectedJuice.ingredients.push(ingredient.name);

        let selectedIngredientEl = document.querySelector(
          ".ingredient.selected .ingredient-img"
        );
        let selectedJuice = document.querySelector(
          ".juice-bottle.selected svg ellipse"
        );
        animIngredientToJuice(selectedIngredientEl, selectedJuice);
      }

      function animIngredientToJuice(element, to) {
        // Get 'first' position
        var firstRect = element.getBoundingClientRect();
        // Get the 'to' position
        var lastRect = to.getBoundingClientRect();
        // Create object with the firstRect values minus the lastRect values
        // To invert the transform
        var invertedRect = {
          top: lastRect.top - firstRect.top,
          left: lastRect.left - firstRect.left,
          width: lastRect.width / firstRect.width,
          height: lastRect.height / firstRect.height
        };
        // Set the transform origin point so it works with the calculated co-ordinates
        element.style.transformOrigin = "left top";
        element.style.zIndex = "100";

        const ingredientToJuice = anime
          .timeline()
          .add({
            targets: element,
            translateY: [
              { value: 30, duration: 200, easing: "easeOutCubic" },
              {
                value: invertedRect.top,
                duration: 200,
                easing: [0.15, 0, 0.2, 0]
              }
            ],
            translateX: [
              { value: 0, duration: 200, easing: "easeOutCubic" },
              {
                value: invertedRect.left,
                duration: 200,
                easing: [0.15, 0, 0.2, 0]
              }
            ],
            rotate: [
              { value: -20, duration: 200, easing: "easeOutCubic" },
              { value: 0, duration: 50, easing: "easeOutSine" }
            ],
            scaleX: [
              { value: 1.2, duration: 200, easing: "easeOutCubic" },
              { value: 0.2, duration: 200, easing: "easeOutSine" }
            ],
            scaleY: [
              { value: 1.2, duration: 200, easing: "easeOutCubic" },
              { value: 0.2, duration: 200, easing: "easeOutSine" }
            ],
            complete: function() {
              element.style.transformOrigin = "50%";
              element.style.opacity = "0";
              element.style.transform = "translateX(0px) translateY(0px)";
            }
          })
          .add({
            targets: ".juice-bottle.selected svg",
            translateX: [
              { value: -20, duration: 50, easing: "easeOutCubic" },
              { value: 0, duration: 500 }
            ],
            translateY: [
              { value: -30, duration: 50, easing: "easeOutCubic" },
              { value: 0, duration: 500 }
            ],
            rotate: [
              { value: -5, duration: 50, easing: "easeOutCubic" },
              { value: 0, duration: 500 }
            ]
          })
          .add({
            targets: element,
            scale: [0.9, 1],
            opacity: 1,
            duration: 500,
            offset: "-=200",
            complete: function() {
              // remove left over inline styles so the swipe transformations work correctly
              // element.style.cssText= "";
              element.style.transformOrigin = "";
            }
          });
      }
    },
    handleScroll: function() {
      // Vars for the things that happen on scrolling
      const bottleSwiper = document.querySelector(".bottle-swiper-wrap");
      const juiceBottleHeight = document.querySelector(".juice-bottle.selected")
        .clientHeight;
      const nav = document.querySelector("#nav");

      // Register the frame
      var animFrame;

      // Listen for scroll events
      window.addEventListener(
        "scroll",
        function(event) {
          // If there's an animation frame waiting to run, cancel it
          if (animFrame) {
            window.cancelAnimationFrame(animFrame);
          }

          // Setup the new requestAnimationFrame()
          animFrame = window.requestAnimationFrame(function() {
            // Run scroll functions
            var scrollAmount = window.pageYOffset;

            // Shrink header on scroll
            // if ( percentScrolled > 90 && !nav.classList.contains('shrink') ) {
            //   nav.classList.add("shrink");
            // } else if ( percentScrolled < 90 && (nav.classList.contains('shrink')) ) {
            //   nav.classList.remove("shrink");
            // }

            // animate perspective origin for parallax effect on hero image
            if (scrollAmount > juiceBottleHeight + 150) {
              bottleSwiper.classList.add("scrolled");
            } else if (scrollAmount < juiceBottleHeight + 5) {
              bottleSwiper.classList.remove("scrolled");
            }
          });
        },
        false
      );
    }
  }
};
</script>

<style scoped lang="scss">
.shop-main-wrap {
  padding: 1px 0 0; // this stops margin collapse from the card element
  position: relative;
  margin: 0 0 200px;
  overflow: hidden;
}

.bottle-swiper-wrap {
  position: absolute;
  // top: 70px;
  // left: 0px;
  // max-height: 180px;
  height: 180px;
  z-index: 100;
  width: 100%;
  &.scrolled {
    position: fixed;
    top: 0;
    left: 0;
    animation: slideDown 1s cubic-bezier(0, 1, 0, 1) both;
  }
}

@keyframes slideDown {
  0% {
    transform: translateY(-400px);
  }
  100% {
    transform: translateY(-100px);
  }
}

.juice-bottle {
  width: 20%;
  display: block;
  position: absolute;
  transition: transform 0.5s cubic-bezier(0.5, 0.5, 0, 0.7);
  transform-origin: 50% 20%;
  top: 10px;
  right: 0;
  .scrolled & {
    opacity: 0;
  }
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
  z-index: 10;
  .scrolled & {
    transition: transform 0s;
    transform: translateX(-400%) scale(1) rotate(0);
    opacity: 1;
  }
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
