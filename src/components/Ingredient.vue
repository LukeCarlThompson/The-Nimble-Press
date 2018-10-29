<template>
  <div 
    :class="['juice-bottle', bottlePosition]">
    <div class="ingredient" 
      v-hammer:pan="onPan">
    </div>
    <p class="ingredient-name">{{this.ingredient.name}}</p>
  </div>
</template>

<script>
import anime from "animejs";

export default {
  name: "Ingredient",
  props: {
    ingredient: Object,
    bottlePosition: String
  },
  computed: {

  },
  watch: {

  },
  methods: {
    onPan: function(e) {
      // select the svg inside our component not the whole component
      var thisBottle = this.$el.querySelector(".ingredient");

      //set z-index so this bottle is in front all the rest
      this.$el.style.zIndex = "2";

      // tone down the movement input then apply it to the bottle
      var rotate = e.deltaX * 0.08;
      thisBottle.style.transform =
        "rotate(" + rotate + "deg) translateY(20%) scale(1.1)";

      // Had to turn off the transition because it was slowing down the movement on mobiles too much
      // Maybe find another method
      // thisBottle.style.transitionDuration = "1s";
      // thisBottle.style.transitionTimingFunction = "cubic-bezier(0, 0.5, 0, 1)";

      // this prop turns true when dragging has finished
      // update counter to move bottle left or right
      // then reset the z-index and transition duration
      // then anim it back to place
      if (e.isFinal) {
        if (e.distance > 40 && e.additionalEvent == "panright") {
          this.$emit("pannedRight");
        } else if (e.distance > 40 && e.additionalEvent == "panleft") {
          this.$emit("pannedLeft");
        }
        this.$el.style.zIndex = "1";
        // thisBottle.style.transitionDuration = "0s";
        anime({
          targets: thisBottle,
          rotate: 0,
          scale: 1,
          translateY: 0,
          duration: 1000,
          complete: function() {
            thisBottle.parentNode.style.zIndex = "0";
          }
        });
      }
    }
  }
};
</script>

<style scoped lang="scss">
.juice-bottle {
  cursor: grab;
  &:active {
    cursor: grabbing;
  }
  .ingredient {
    width: 140%;
    height: 200px;
    margin-left: -20%;
    transform-origin: 50% 200%;
    background-color: pink;
    border-radius: 200px;
    @media screen and (max-width: 530px) {
      height: 50vw;
    }
  }
}

.colored-shadow {
  opacity: 0;
  transition: opacity 1s;
  transition-delay: 0.2s;
  .selected & {
    opacity: 1;
  }
}

.ingredient-name {
  font-weight: 500;
  font-size: 1.2rem;
}

.top-color {
  stop-color: var(--top-color);
}
.bottom-color {
  stop-color: var(--bottom-color);
}
</style>
