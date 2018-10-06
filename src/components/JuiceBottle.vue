<template>
  <div 
    :class="['juice-bottle', bottlePosition]"
    :style="gradientColors">
    <svg 
      v-hammer:pan="onPan"
      xmlns="http://www.w3.org/2000/svg"
      xmlns:xlink="http://www.w3.org/1999/xlink" 
      width="130" 
      height="250"
      viewBox="0 0 130 250" >
      <defs>
        <filter 
          id="filter-1" 
          width="400%" 
          height="800%" 
          x="-100%" 
          y="-400%" 
          >
          <feDropShadow dx="5" dy="5" stdDeviation="8" flood-color="grey" flood-opacity="0.3" />
        </filter>
        <filter 
          :id="blurFilterId" 
          width="200%" 
          height="800%" 
          x="-50%" 
          y="-400%" 
          >
          <feGaussianBlur stdDeviation="15" />
        </filter>
        <linearGradient 
          :id="uniqueId" 
          x1="50%" 
          x2="50%" 
          y1="0%" 
          y2="100%">
          <stop 
            offset="0%" 
            class="top-color"/>
          <stop 
            offset="100%" 
            class="bottom-color"/>
        </linearGradient>
        <linearGradient 
          id="linearGradient-5" 
          x1="0%" 
          x2="79.8%" 
          y1="41%" 
          y2="41%">
          <stop 
            offset="0%" 
            stop-color="#55DFFF" 
            stop-opacity="0"/>
          <stop 
            offset="29.2%" 
            stop-color="#FFF" 
            stop-opacity=".6"/>
          <stop 
            offset="100%" 
            stop-color="#77DBFF" 
            stop-opacity="0"/>
        </linearGradient>
        <linearGradient 
          id="linearGradient-6" 
          x1="39.9%" 
          x2="39.9%" 
          y1="5.9%" 
          y2="24%">
          <stop 
            offset="0%" 
            stop-color="#FFF" 
            stop-opacity="0"/>
          <stop 
            offset="29.2%" 
            stop-color="#FFF" 
            stop-opacity=".6"/>
          <stop 
            offset="100%" 
            stop-color="#FFF" 
            stop-opacity="0"/>
        </linearGradient>
        <path 
          id="path-7" 
          d="M-3.9-1.8h115.2v202.4H-3.9z"/>
        <radialGradient 
          id="radialGradient-8" 
          cx="29.1%" 
          cy="18.6%" 
          r="87.2%" 
          fx="29.1%" 
          fy="18.6%" 
          gradientTransform="scale(1 .96) rotate(61.1 .3 .2)">
          <stop 
            offset="0%" 
            stop-color="#CEAAF4"/>
          <stop 
            offset="50.8%" 
            stop-color="#9C75C5"/>
          <stop 
            offset="100%" 
            stop-color="#5C3586"/>
        </radialGradient>
        <ellipse 
          id="path-9" 
          cx="8.3" 
          cy="8.6" 
          rx="8.3" 
          ry="8.6"/>
        <linearGradient 
          id="linearGradient-11" 
          x1="50%" 
          x2="62.8%" 
          y1="0%" 
          y2="67%">
          <stop 
            offset="0%" 
            stop-color="#9FE3DA"/>
          <stop 
            offset="56.4%" 
            stop-color="#66C2B3"/>
          <stop 
            offset="100%" 
            stop-color="#45AA99"/>
        </linearGradient>
        <linearGradient 
          id="linearGradient-12" 
          x1="50%" 
          x2="50%" 
          y1="0%" 
          y2="79.5%">
          <stop 
            offset="0%" 
            stop-color="#9FE3DA"/>
          <stop 
            offset="56.4%" 
            stop-color="#66C2B3"/>
          <stop 
            offset="100%" 
            stop-color="#45AA99"/>
        </linearGradient>
        <clipPath 
          :id="bottleOutlineId" 
          fill="#fff">
          <path 
            id="path-2" 
            d="M 35.33 0 C 35.33 23.66 0 13.14 0 43.38 L 0 187.44 C 0 200.59 106 199.8 106 186.65 L 106 43.38 C 106 13.14 70.67 23.66 70.67 0 L 35.33 0 Z"/>
        </clipPath>
        <path 
          id="path-13" 
          d="M22 14.6h1v.4l.6-.4.6-.1c.4 0 .8.1 1 .4.3.3.4.7.4 1.1v2.8h-1V17v-1l-.3-.4a.6.6 0 0 0-.4-.1c-.2 0-.4 0-.5.2-.2.1-.3.3-.3.6l-.1.8v1.7h-1v-4.2zm5-1.7c.2 0 .4 0 .5.2.2.1.2.3.2.5s0 .3-.2.4c-.1.2-.3.2-.4.2-.2 0-.4 0-.5-.2a.7.7 0 0 1-.2-.5c0-.1 0-.3.2-.4.1-.2.3-.2.5-.2zm-.5 1.7h1v4.2h-1v-4.2zm2 0h1v.5l.6-.5.8-.1a1.3 1.3 0 0 1 1.2.8c.1-.3.3-.5.6-.6a1.6 1.6 0 0 1 1.5 0c.3.1.4.3.5.6l.2 1v2.5h-1v-2.1c0-.5-.1-.8-.3-1 0-.2-.3-.2-.5-.2l-.5.1a1 1 0 0 0-.3.4v2.8h-1.1v-2L31 16c0-.2-.2-.3-.3-.4a.6.6 0 0 0-.4-.1l-.4.1a1 1 0 0 0-.3.5l-.1.8v2h-1v-4.3zM37 13v2l.6-.4.7-.1c.5 0 1 .2 1.4.6.3.4.5 1 .5 1.6 0 .7-.2 1.2-.6 1.6a1.8 1.8 0 0 1-2 .5 2 2 0 0 1-.6-.4v.4h-1V13h1zm1 2.5a1 1 0 0 0-.7.3c-.3.2-.4.5-.4 1 0 .3.1.6.4.8.2.2.4.4.8.4.3 0 .6-.2.8-.4.2-.2.3-.5.3-.9l-.3-.9a1 1 0 0 0-.8-.3zm3-2.5h1v5.8h-1V13zm6.1 4h-3.3c0 .3.2.6.4.7.2.2.4.3.8.3s.7-.1 1-.4l.8.4a2 2 0 0 1-1.8 1 2.1 2.1 0 0 1-2.2-2.3c0-.6.2-1.1.6-1.6a2 2 0 0 1 1.5-.6c.7 0 1.2.2 1.6.6.4.5.6 1 .6 1.7v.2zm-1-.8a1 1 0 0 0-.4-.6l-.7-.2c-.3 0-.6 0-.8.2l-.4.6H46zM23 21v.4l.6-.4.7-.2c.6 0 1 .3 1.4.7.4.4.6 1 .6 1.6 0 .6-.2 1.1-.6 1.5a1.8 1.8 0 0 1-2 .6 2 2 0 0 1-.7-.5v2h-1v-5.7h1zm1 .8a1 1 0 0 0-.7.4c-.2.2-.3.5-.3.9 0 .3 0 .6.3.9.2.2.5.3.8.3.3 0 .6-.1.8-.3.2-.3.3-.6.3-1 0-.3 0-.6-.3-.8a1 1 0 0 0-.8-.4zm2.9-.8h.9v.5c0-.2.2-.4.3-.5a1 1 0 0 1 1 0l-.3.9-.3-.1c-.2 0-.3 0-.4.3l-.2 1.2v1.9h-1V21zm6.9 2.4h-3.4c0 .3.2.5.4.7.2.2.5.3.8.3.4 0 .7-.2 1-.5l.9.5a2 2 0 0 1-1.9.9 2.1 2.1 0 0 1-2.2-2.2c0-.7.2-1.2.6-1.6a2 2 0 0 1 1.6-.7c.6 0 1.1.3 1.6.7.4.4.6 1 .6 1.7v.2zm-1-.9a1 1 0 0 0-.5-.5c-.2-.2-.4-.3-.7-.3-.3 0-.5.1-.8.3l-.3.5h2.2zm4.3-1l-.6.7c-.3-.3-.5-.4-.7-.4h-.3a.2.2 0 0 0 0 .4l.3.2.4.2.8.6.2.8c0 .3-.1.7-.4 1-.3.2-.6.3-1 .3-.7 0-1.2-.3-1.5-.7l.6-.7.4.3.5.1h.3l.1-.3c0-.2-.1-.3-.4-.5l-.4-.2c-.6-.3-1-.7-1-1.2 0-.4.2-.7.4-.9.3-.2.6-.4 1-.4a1.7 1.7 0 0 1 1.3.7zm3.5 0l-.7.7c-.2-.3-.5-.4-.7-.4H39a.2.2 0 0 0 0 .4l.3.2.4.2.8.6c.2.2.2.5.2.8 0 .3 0 .7-.4 1-.2.2-.6.3-1 .3-.7 0-1.1-.3-1.5-.7l.6-.7.5.3.4.1h.3l.2-.3c0-.2-.2-.3-.5-.5l-.3-.2c-.7-.3-1-.7-1-1.2 0-.4 0-.7.3-.9.3-.2.6-.4 1-.4a1.7 1.7 0 0 1 1.4.7zM21.8 8h.6v.9h.4v.5h-.4v2h-.6v-2h-.3v-.5h.3v-1zm1.3 0h.6V9l.4-.2.3-.1c.3 0 .5 0 .6.2.2.2.3.4.3.7v1.6h-.6v-1-.6l-.2-.3h-.3-.3l-.2.4v1.5h-.6V7.8zm5.2 2.3h-2l.2.4.5.1c.2 0 .4 0 .6-.2l.5.2a1.2 1.2 0 0 1-1 .6 1.2 1.2 0 0 1-1.4-1.3c0-.4.1-.7.4-1 .2-.2.5-.3.9-.3s.7.1 1 .4c.1.2.3.5.3 1zm-.6-.5c0-.2-.2-.3-.3-.4a.7.7 0 0 0-.4 0h-.4l-.3.4h1.4z"/>
      </defs>
      <ellipse
          style="fill: var(--bottom-color);"
          :filter="'url(#' + blurFilterId + ')'"
          cx="65" cy="197" rx="30"
          ry="20"/>
      <g 
        id="juice-bottle" 
        filter="url(#filter-1)"
        fill="none" 
        fill-rule="evenodd">
        <g 
          id="bottle" 
          :clip-path="'url(#' + bottleOutlineId + ')'" 
          transform="translate(12 22)" >
          <path
            id="bottle-outline" 
            fill="#D8D8D8"
            opacity="0.5"
            fill-rule="nonzero"
            d="M 35.33 0 C 35.33 23.66 0 13.14 0 43.38 L 0 187.44 C 0 200.59 106 199.8 106 186.65 L 106 43.38 C 106 13.14 70.67 23.66 70.67 0 L 35.33 0 Z" />
          <path 
            id="Juice-Color" 
            :fill="'url(#'+ uniqueId +')'" 
            fill-rule="nonzero" 
            d="M-3.9 20.5h115.2v180.1H-3.9z" />
          <g 
            id="Glass-sheen" 
            fill-rule="nonzero" >
            <use 
              fill="url(#linearGradient-5)" 
              fill-opacity=".8" 
              xlink:href="#path-7"/>
            <use 
              fill="url(#linearGradient-6)" 
              xlink:href="#path-7" 
              style="mix-blend-mode:screen"/>
          </g>
        </g>
        <path 
          id="bottle-lid" 
          fill="#4A4A4A" 
          fill-rule="nonzero" 
          d="M40.8 15c0-5.3 48.4-5.3 48.4 0V24H40.8V15z"/>
        <g 
          id="bottle-label"
          style="transform: translateX(27.7px) translateY(75.4px);">
          <path 
            id="label-bg" 
            fill="#FFF" 
            fill-rule="nonzero" 
            d="M13.4 0h50.5c1 0 1.3.1 1.7.4.4.2.6.5.8 1 .2.4.3.8.3 2v81.3c0 1.2 0 1.6-.3 2-.2.5-.4.8-.8 1-.4.2-.7.4-1.7.4H13.4c-1 0-1.4-.2-1.8-.4-.3-.2-.6-.5-.8-1-.2-.4-.3-.8-.3-2V3.4c0-1.2 0-1.6.3-2 .2-.5.5-.8.8-1 .4-.3.8-.4 1.8-.4z"/>
          <g 
            id="Ingredients-list" 
            fill="#D8D8D8" 
            fill-rule="nonzero" 
            transform="translate(22.2 32.9)">
            <path 
              id="Rectangle-4" 
              d="M0 0h31.4v5.3H0z"/>
            <path 
              id="Rectangle-4-Copy" 
              d="M0 9.2h26.2v2.6H0z"/>
            <path 
              id="Rectangle-4-Copy-2" 
              d="M0 15.8h28.8v2.6H0z"/>
            <path 
              id="Rectangle-4-Copy-3" 
              d="M0 22.3h32.7v2.6H0z"/>
            <path 
              id="Rectangle-4-Copy-4" 
              d="M0 28.9h31.4v2.6H0z"/>
            <path 
              id="Rectangle-4-Copy-5" 
              d="M0 35.5h34v2.6H0z"/>
            <path 
              id="Rectangle-4-Copy-6" 
              d="M0 42.1h28.8v2.6H0z"/>
          </g>
          <g 
            id="fruit" 
            transform="translate(0 4)">
            <g 
              id="Fruit" 
              transform="translate(2.9 8.8)">
              <mask 
                id="mask-10" 
                fill="#fff">
                <use xlink:href="#path-9"/>
              </mask>
              <g 
                id="Oval" 
                fill-rule="nonzero">
                <use 
                  fill="url(#radialGradient-8)" 
                  xlink:href="#path-9"/>
                <use 
                  fill="#F56F23" 
                  xlink:href="#path-9" 
                  style="mix-blend-mode:color"/>
              </g>
              <path 
                id="Path-3-Copy-3" 
                fill="#A9A9A9" 
                fill-rule="nonzero" 
                d="M15.1-4.7C10.4-6 7.6.3 9.8 5.7c6-1.7 7.8-8.4 5.3-10.4z" 
                mask="url(#mask-10)" 
                style="mix-blend-mode:multiply"/>
              <path 
                id="Path-3-Copy-4" 
                fill="#A9A9A9" 
                fill-rule="nonzero" 
                d="M1.8 1.4c-4.1 0-6.1 6.3-2.5 10.4C3 8 4.5 2.8 1.8 1.4z" 
                mask="url(#mask-10)" 
                style="mix-blend-mode:multiply"/>
              <ellipse 
                id="Oval-2" 
                cx="5.6" 
                cy="4" 
                fill="#FFF" 
                fill-rule="nonzero" 
                mask="url(#mask-10)" 
                rx="1.1" 
                ry="1.2"/>
            </g>
            <path 
              id="Path-3" 
              fill="url(#linearGradient-11)" 
              fill-rule="nonzero" 
              d="M17.6 3.4c-4.7-1.2-7.5 5-5.3 10.3 6-1.6 7.8-8.2 5.3-10.3z"/>
            <path 
              id="Path-3-Copy-2" 
              fill="url(#linearGradient-11)" 
              fill-rule="nonzero" 
              d="M10.7 1C7-.9 1.4 4.1 3.6 9.2c5.7-1 9.8-6.4 7-8.2z" 
              transform="rotate(8 7.3 5)"/>
            <path 
              id="Path-3-Copy" 
              fill="url(#linearGradient-12)" 
              fill-rule="nonzero" 
              d="M4.3 10c-4 0-6 6.2-2.4 10.3 3.7-3.8 5.2-9 2.4-10.3z"/>
          </g>
          <mask 
            id="mask-14" 
            fill="#fff">
            <use xlink:href="#path-13"/>
          </mask>
          <use 
            id="text" 
            fill="#1E1E1E" 
            xlink:href="#path-13"/>
        </g>
      </g>
    </svg>
  </div>
</template>

<script>
import anime from "animejs";

export default {
  name: "JuiceBottle",
  props: {
    juice: Object,
    bottlePosition: String
  },
  data: function() {
    return {
      sizeData: [
        { size: "small",
          path:
            "M 35.544 47.45 C 35.544 66.613 10.576 70.407 10.576 94.9 L 10.576 187.929 C 10.576 198.58 95.184 198.58 95.184 187.929 L 95.184 94.9 C 95.184 70.407 71.088 66.613 71.088 47.45 L 35.544 47.45 Z",
          lidY: 45,
          labelY: 100,
          juiceColorScaleY: 0.85
        },
        { size: "medium",
          path:
            "M 35.33 0 C 35.33 23.66 10.576 19.215 10.576 49.455 L 10.576 187.929 C 10.576 201.079 95.184 201.079 95.184 187.929 L 95.184 49.455 C 95.184 19.215 70.67 23.66 70.67 0 L 35.33 0 Z",
          lidY: 0,
          labelY: 75.4,
          juiceColorScaleY: 1
        },
        { size: "large",
          path:
            "M 35.33 0 C 35.33 23.66 0 13.14 0 43.38 L 0 187.44 C 0 200.59 106 199.8 106 186.65 L 106 43.38 C 106 13.14 70.67 23.66 70.67 0 L 35.33 0 Z",
          lidY: 0,
          labelY: 75.4,
          juiceColorScaleY: 1
        }
      ]
    };
  },
  computed: {
    uniqueId: function() {
      // replace all spaces with _ and add a random number between 1 and 100 on the end
      const juiceComputedId =
        this.juice.name.replace(/\s/g, "_") +
        Math.floor(Math.random() * 1000 + 1);
      return juiceComputedId;
    },
    bottleOutlineId: function() {
      // create a unique ID so I can change the path of one bottle and not have it effect the masks of the other SVG's that use the same ID.
      return (
        "bottle-outline" +
        this.juice.name.replace(/\s/g, "_") +
        Math.floor(Math.random() * 1000 + 1)
      );
    },
    blurFilterId: function() {
      // create a unique ID so I can change the path of one bottle and not have it effect the masks of the other SVG's that use the same ID.
      return (
        "filter-" +
        this.juice.name.replace(/\s/g, "_") +
        Math.floor(Math.random() * 1000 + 1)
      );
    },
    gradientColors: function() {
      return {
        "--top-color": this.juice.color.top,
        "--bottom-color": this.juice.color.bottom
      };
    }
  },
  watch: {
    'juice.size': function(value) {
      // this function runs when the juiceSize prop changes

      // get all the elements to animate
      const bottleOutline = this.$el.querySelector("#path-2");
      const bottleLid = this.$el.querySelector("#bottle-lid");
      const bottleLabel = this.$el.querySelector("#bottle-label");
      const juiceColor = this.$el.querySelector("#Juice-Color");

      // Get the new values to animate to from the sizeData array
      let newSize = this.sizeData[value];

      // stop any animations that might be currently playing
      anime.remove(this.$el.querySelector("svg"), bottleOutline, juiceColor, bottleLabel, bottleLid);

      anime.timeline()
        .add({
          targets: this.$el.querySelector("svg"),
          begin: function(anim) {
            anim.animatables[0].target.style.transformOrigin = "50% 50%";
          },
          skewX: [10, -8, 5, 0],
          rotate: [12, -8, 5, 0],
          duration: 300,
          easing: "easeOutQuart",
          complete: function(anim) {
            anim.animatables[0].target.style.transformOrigin = "";
          },
          offset: 0
        })
        .add({
          targets: bottleOutline,
          d: [{ value: newSize.path }],
          offset: 200
        })
        .add({
          targets: juiceColor,
          begin: function(anim) {
            anim.animatables[0].target.style.transformOrigin = "50% 100%";
          },
          scaleY: newSize.juiceColorScaleY,
          offset: 200
        })
        .add({
          targets: bottleLabel,
          translateX: [27.7, 27.7],
          translateY: newSize.labelY,
          offset: 150
        })
        .add({
          targets: bottleLid,
          translateY: newSize.lidY,
          offset: 250
        });
    }
  },
  methods: {
    onPan: function(e) {
      // select the svg inside our component not the whole component
      var thisBottle = this.$el.querySelector("svg");

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
  svg {
    width: 140%;
    margin-left: -20%;
    transform-origin: 50% 200%;
    @media screen and (max-width: 530px) {
      height: 50vw;
    }
  }
}
.top-color {
  stop-color: var(--top-color);
}
.bottom-color {
  stop-color: var(--bottom-color);
}
</style>
