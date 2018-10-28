<template>
  <div class="bottle-swiper-wrap">
    <JuiceBottle
      v-for="(juice, i) in juices"
      :bottle-position="bottlePosition(i)"
      :juice="juice"
      :key="juice.name"
      @pannedRight="decrementCounter"
      @pannedLeft="incrementCounter"/>
    <juiceInfoCard :juice-info="selectedJuice"
      @changeBottleSize="changeBottleSize"/>

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
          name: "Pomegranite Twist",
          size: "2",
          selected: false,
          ingredients: ["Pomegranite", "Green Apple", "Lime"],
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
      for(let i = 0; this.juices.length > i; i++) {
        if (this.juices[i].selected == true) {
          this.juices[i].size = value;
        }
      }
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
