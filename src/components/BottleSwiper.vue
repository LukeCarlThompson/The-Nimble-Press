<template>
  <div class="bottle-swiper-wrap">
    <JuiceBottle
      v-for="(juice, i) in juices"
      :juice-color="juice.color"
      :bottle-position="bottlePosition(i)"
      :juice-name="juice.name"
      :key="juice.name"
      @pannedRight="decrementCounter"
      @pannedLeft="incrementCounter"/>
    <juiceInfoCard :juice-info="selectedJuice" />

  </div>
</template>

<script>
// @ is an alias to /src
import JuiceBottle from "@/components/JuiceBottle.vue";
import JuiceInfoCard from "@/components/JuiceInfoCard.vue";

export default {
  name: "BottleSwiper",
  components: {
    JuiceBottle,
    JuiceInfoCard
  },
  data() {
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
          name: "Orange Juice",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#F6D663",
            bottom: "#F77C1C"
          }
        },
        {
          name: "Green Juice",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#B4EC51",
            bottom: "#429321"
          }
        },
        {
          name: "Green Juice 02",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#B4EC51",
            bottom: "#429321"
          }
        },
        {
          name: "Red Juice",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#FDA0A8",
            bottom: "#DF0B2B"
          }
        },
        {
          name: "Purple Juice",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#A664B1",
            bottom: "#473E9D"
          }
        },
        {
          name: "Purple Juice 02",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#A664B1",
            bottom: "#473E9D"
          }
        },
        {
          name: "Purple Juice 03",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#A664B1",
            bottom: "#473E9D"
          }
        },
        {
          name: "Purple Juice 04",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#A664B1",
            bottom: "#473E9D"
          }
        },
        {
          name: "Red Juice 02",
          ingredients: ["ingedient 01", "ingedient 02", "ingredient 03"],
          color: {
            top: "#FDA0A8",
            bottom: "#DF0B2B"
          }
        },
      ],
      selectedJuice: Object
    };
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
      if (this.counter <= - (this.juices.length -4)) {
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
        classIndex = this.classes.length -1;
      }

      // if classIndex puts bottle in the middle then set it to be the selected juice prop
      // this juice gets sent to the juiceInfoCard component
      if (this.classes[classIndex] == "selected") {
        this.selectedJuice = this.juices[i];
      }

      // return the appropriate class from the classes array
      return this.classes[classIndex];
    }
  }
};
</script>

<style scoped lang="scss">
.bottle-swiper-wrap {
  overflow: hidden; // this stops margin collapse from the card element
  position: relative;
}

.juice-bottle {
  width: 20%;
  display: block;
  position: absolute;
  transition: transform 0.5s cubic-bezier(0.5, 0.5, 0, 0.7);
  transform-origin: 50% 20%;
  top: 10px;
  right: 0;
}

.off-screen-left {
  transform: translateX(-500%) scale(0.3) rotate(15deg);
}
.far-left {
  transform: translateX(-400%) scale(0.5) rotate(0);
}
.left {
  transform: translateX(-320%) scale(0.7) rotate(0);
}
.selected {
  transform: translateX(-200%) scale(1.2) rotate(0);
}
.right {
  transform: translateX(-80%) scale(0.7) rotate(0);
}
.far-right {
  transform: translateX(0) scale(0.5) rotate(0);
}
.off-screen-right {
  transform: translateX(100%) scale(0.3) rotate(-15deg);
}
</style>
