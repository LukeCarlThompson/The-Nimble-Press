<template>
  <div 
    :class="['ingredient', bottlePosition]">
    <div 
      v-hammer:pan="onPan"
      :style="{backgroundImage: 'url(' + backgroundImage + ')'}"
      class="ingredient-img">
    </div>
    <transition name="fade">
      <p 
        v-if="ingredient.selected" 
        class="ingredient-name">{{ ingredient.name }}</p>
    </transition>
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
    backgroundImage: function() {
      return "/images/" + this.ingredient.name.replace(/\s+/, "") + ".svg";
    }
  },
  watch: {},
  methods: {
    onPan: function(e) {
      // select the svg inside our component not the whole component
      var thisBottle = this.$el.querySelector(".ingredient-img");

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
.ingredient {
  cursor: grab;
  &:active {
    cursor: grabbing;
  }
  .ingredient-img {
    width: 140%;
    height: 200px;
    margin-left: -20%;
    transform-origin: 50% 200%;
    // background-color: pink;
    // border-radius: 200px;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: 50%;
    @media screen and (max-width: 530px) {
      height: 50vw;
    }
    svg {
      max-height: 100%;
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

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
