<template>
  <div class="bottle-swiper-wrap">
      <!-- <li class="list-item" v-for="juice in juices" :key="juice.name">
        <JuiceBottle :juiceColor="juice.color"/>
      </li> -->
      <!-- <li class="list-item" v-for="(data, index) in skills" :key="data.skill"> -->
      <!-- <JuiceBottle v-for="(juice, i) in juices" :juiceColor="juices[i].color" :key="i"/> -->
      <JuiceBottle
        v-for="(juice, i) in juices"
        v-on:incrementCounter="counter += 1"
        v-on:decrementCounter="counter -= 1"
        :juiceColor="juice.color"
        :bottlePosition="bottlePosition(i)"
        :juiceName="juice.name"
        :key="juice.name"/>
      <juiceInfoCard :juiceInfo="juiceInfo()" />

  </div>
</template>

<script>
// @ is an alias to /src
import JuiceBottle from "@/components/JuiceBottle.vue";
import JuiceInfoCard from "@/components/JuiceInfoCard.vue";

export default {
  name: "bottleSwiper",
  components: {
    JuiceBottle,
    JuiceInfoCard
  },
  methods: {
    moveBottles() {
      this.counter += 1;
      console.log(this.counter);
    },
    bottlePosition(i) {

      if (this.counter == this.juices.length) {
        this.counter = 0;
      }
      
      return (this.counter + i) < 7 ? this.classes[this.counter + i ] : 'off-screen-right';

    },
  juiceInfo() {
    return this.juices[this.counter]
  },
  },
  data() {
    return {
      counter: 0,
      classes: [
        'off-screen-left',
        'far-left',
        'left',
        'selected',
        'right',
        'far-right',
        'off-screen-right',
      ],
      juices: [
        {
          name: 'Orange Juice',
          ingredients: [
            'ingedient 01',
            'ingedient 02',
            'ingredient 03'
          ],
          color: {
            top: '#F6D663',
            bottom: '#F77C1C',
          }
        },
        {
          name: 'Green Juice',
          ingredients: [
            'ingedient 01',
            'ingedient 02',
            'ingredient 03'
          ],
          color: {
            top: '#B4EC51',
            bottom: '#429321',
          }
        },
        {
          name: 'Red Juice',
          ingredients: [
            'ingedient 01',
            'ingedient 02',
            'ingredient 03'
          ],
          color: {
            top: '#FDA0A8',
            bottom: '#DF0B2B',
          }
        },
        {
          name: 'Purple Juice',
          ingredients: [
            'ingedient 01',
            'ingedient 02',
            'ingredient 03'
          ],
          color: {
            top: '#A664B1',
            bottom: '#473E9D',
          }
        },
        {
          name: 'Purple Juice 02',
          ingredients: [
            'ingedient 01',
            'ingedient 02',
            'ingredient 03'
          ],
          color: {
            top: '#A664B1',
            bottom: '#473E9D',
          }
        },
        {
          name: 'Purple Juice 03',
          ingredients: [
            'ingedient 01',
            'ingedient 02',
            'ingredient 03'
          ],
          color: {
            top: '#A664B1',
            bottom: '#473E9D',
          }
        }
      ],
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
