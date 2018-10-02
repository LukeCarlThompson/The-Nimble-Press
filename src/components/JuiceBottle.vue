<template>
  <div 
    :class="['juice-bottle', bottlePosition, juiceColor]"
    :style="gradientColors">
    <svg 
      v-hammer:pan="onPan"
      xmlns="http://www.w3.org/2000/svg" 
      xmlns:xlink="http://www.w3.org/1999/xlink" 
      width="130" 
      height="200" 
      viewBox="0 0 130 250">
      <defs>
        <filter 
          id="filter-1" 
          width="133%" 
          height="117.2%" 
          x="-16.5%" 
          y="-6%" 
          filterUnits="objectBoundingBox">
          <feOffset 
            dy="5" 
            in="SourceAlpha" 
            result="shadowOffsetOuter1"/>
          <feGaussianBlur 
            in="shadowOffsetOuter1" 
            result="shadowBlurOuter1" 
            stdDeviation="5"/>
          <feColorMatrix 
            in="shadowBlurOuter1" 
            result="shadowMatrixOuter1" 
            values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.2 0"/>
          <feMerge>
            <feMergeNode in="shadowMatrixOuter1"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>
        <path 
          id="path-2" 
          d="M35.33 0C35.33 23.66 0 13.14 0 43.38v143.27c0 13.15 106 13.15 106 0V43.38C106 13.14 70.67 23.66 70.67 0H35.33z"/>
        <linearGradient 
          :id="uniqueId" 
          x1="50%" 
          x2="50%" 
          y1="0%" 
          y2="100%">
          <stop 
            offset="0%" 
            class="top-color" />
          <stop 
            offset="100%" 
            class="bottom-color" />
        </linearGradient>
        <linearGradient 
          id="linearGradient-5" 
          x1="0%" 
          x2="79.82%" 
          y1="40.97%" 
          y2="40.97%">
          <stop 
            offset="0%" 
            stop-color="#55DFFF" 
            stop-opacity="0"/>
          <stop 
            offset="29.23%" 
            stop-color="#FFF" 
            stop-opacity=".55"/>
          <stop 
            offset="100%" 
            stop-color="#77DBFF" 
            stop-opacity="0"/>
        </linearGradient>
        <linearGradient 
          id="linearGradient-6" 
          x1="39.91%" 
          x2="39.91%" 
          y1="5.86%" 
          y2="24.04%">
          <stop 
            offset="0%" 
            stop-color="#FFF" 
            stop-opacity="0"/>
          <stop 
            offset="29.23%" 
            stop-color="#FFF" 
            stop-opacity=".55"/>
          <stop 
            offset="100%" 
            stop-color="#FFF" 
            stop-opacity="0"/>
        </linearGradient>
        <path 
          id="path-7" 
          d="M-3.93-2.63h115.16V199.8H-3.93z"/>
        <radialGradient 
          id="radialGradient-8" 
          cx="29.05%" 
          cy="18.64%" 
          r="86.61%" 
          fx="29.05%" 
          fy="18.64%" 
          gradientTransform="matrix(.48654 .84605 -.87366 .47116 .31 -.15)">
          <stop 
            offset="0%" 
            stop-color="#CEAAF4"/>
          <stop 
            offset="50.84%" 
            stop-color="#9C75C5"/>
          <stop 
            offset="100%" 
            stop-color="#5C3586"/>
        </radialGradient>
        <ellipse 
          id="path-9" 
          cx="8.26" 
          cy="8.53" 
          rx="8.26" 
          ry="8.53"/>
        <linearGradient 
          id="linearGradient-11" 
          x1="50%" 
          x2="62.81%" 
          y1="0%" 
          y2="67.01%">
          <stop 
            offset="0%" 
            stop-color="#9FE3DA"/>
          <stop 
            offset="56.36%" 
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
          y2="79.54%">
          <stop 
            offset="0%" 
            stop-color="#9FE3DA"/>
          <stop 
            offset="56.36%" 
            stop-color="#66C2B3"/>
          <stop 
            offset="100%" 
            stop-color="#45AA99"/>
        </linearGradient>
        <path 
          id="path-13" 
          d="M.53 6.8h1.05v.42c.24-.2.46-.33.65-.41.2-.08.4-.12.6-.12.41 0 .77.14 1.06.43.24.25.36.61.36 1.1v2.75H3.21V9.14c0-.5-.02-.83-.06-1a.68.68 0 0 0-.24-.37.66.66 0 0 0-.41-.12.8.8 0 0 0-.55.2c-.16.15-.26.35-.32.6-.03.13-.05.41-.05.85v1.67H.53V6.8zm5.15-1.72c.19 0 .35.06.48.2a.67.67 0 0 1 0 .96.64.64 0 0 1-.47.2.65.65 0 0 1-.48-.2.67.67 0 0 1-.2-.5c0-.18.07-.34.2-.47.13-.13.29-.2.47-.2zM5.16 6.8H6.2v4.17H5.16V6.8zm2 0H8.2v.48a1.76 1.76 0 0 1 1.32-.59 1.34 1.34 0 0 1 1.22.75 1.68 1.68 0 0 1 2.2-.55c.23.15.39.33.49.55.1.22.15.58.15 1.08v2.45h-1.06V8.86c0-.48-.06-.8-.18-.97a.63.63 0 0 0-.53-.25.81.81 0 0 0-.49.16.9.9 0 0 0-.31.42c-.07.18-.1.47-.1.87v1.88H9.84V8.95c0-.37-.03-.64-.08-.81a.73.73 0 0 0-.25-.38.66.66 0 0 0-.4-.12.8.8 0 0 0-.48.16.93.93 0 0 0-.32.43c-.07.19-.1.48-.1.89v1.85H7.15V6.8zm8.48-1.61v2.07a1.78 1.78 0 0 1 1.33-.57c.54 0 1 .2 1.39.62.38.41.57.94.57 1.58 0 .63-.2 1.15-.6 1.56a1.87 1.87 0 0 1-2.07.5 1.8 1.8 0 0 1-.62-.42v.44h-1.05V5.2h1.05zm1.1 2.47c-.33 0-.6.11-.82.34-.22.22-.33.51-.33.88s.1.67.33.9c.22.23.5.34.82.34.32 0 .6-.11.81-.35.22-.23.33-.53.33-.89s-.1-.65-.32-.88a1.08 1.08 0 0 0-.82-.34zm2.95-2.47h1.06v5.78h-1.06V5.2zm6.21 4h-3.38c.05.3.18.53.4.7.2.18.47.27.8.27.4 0 .73-.14 1.02-.41l.88.41a2.1 2.1 0 0 1-.79.7c-.3.15-.67.22-1.1.22-.66 0-1.2-.2-1.6-.62a2.1 2.1 0 0 1-.63-1.55 2.15 2.15 0 0 1 2.17-2.22c.66 0 1.2.21 1.62.63.4.42.62.98.62 1.67v.2zm-1.05-.83a1.01 1.01 0 0 0-.42-.56 1.2 1.2 0 0 0-.7-.22c-.3 0-.56.08-.78.24-.14.1-.27.29-.38.54h2.28zM1.58 13.2v.46a1.78 1.78 0 0 1 1.33-.57c.54 0 1 .2 1.39.62.38.4.58.94.58 1.58 0 .62-.2 1.14-.6 1.56a1.87 1.87 0 0 1-2.08.5 1.8 1.8 0 0 1-.62-.42v1.97H.53v-5.7h1.05zm1.1.86c-.33 0-.6.1-.82.33-.22.23-.33.52-.33.89s.11.67.33.9c.22.23.5.34.82.34.33 0 .6-.12.82-.35.22-.23.33-.53.33-.89s-.11-.65-.33-.88a1.08 1.08 0 0 0-.82-.34zm2.82-.86h.9v.52c.1-.2.23-.36.4-.47a.94.94 0 0 1 .95-.05l-.33.9a.73.73 0 0 0-.3-.1c-.16 0-.3.1-.41.3-.11.2-.17.6-.17 1.18v1.9H5.5V13.2zm6.98 2.39H9.09c.05.3.18.53.4.7.2.18.48.27.8.27.4 0 .74-.14 1.02-.41l.89.41a2.1 2.1 0 0 1-.8.7c-.3.14-.67.22-1.1.22-.65 0-1.19-.2-1.6-.62a2.1 2.1 0 0 1-.62-1.55c0-.64.2-1.17.62-1.6.4-.41.93-.62 1.55-.62.66 0 1.2.2 1.61.63.41.42.62.98.62 1.67v.2zm-1.06-.83c-.07-.23-.2-.42-.41-.57a1.2 1.2 0 0 0-.71-.22c-.3 0-.55.09-.77.25-.14.1-.27.28-.39.54h2.28zm4.48-.98l-.65.65c-.27-.26-.5-.4-.73-.4a.46.46 0 0 0-.27.08.22.22 0 0 0-.1.19c0 .05.02.1.06.15.04.05.15.11.31.2l.39.19c.4.2.69.4.84.6.15.22.22.46.22.74 0 .37-.13.68-.4.93a1.6 1.6 0 0 1-1.1.37c-.62 0-1.1-.24-1.47-.71l.65-.7c.12.14.26.25.43.34.17.09.31.13.44.13.14 0 .25-.03.34-.1a.28.28 0 0 0 .12-.23c0-.16-.15-.32-.46-.47l-.35-.18c-.68-.34-1.02-.76-1.02-1.27 0-.33.13-.62.39-.85.25-.24.58-.35.98-.35a1.71 1.71 0 0 1 1.38.69zm3.47 0l-.65.65c-.26-.26-.5-.4-.72-.4a.46.46 0 0 0-.28.08.22.22 0 0 0-.1.19c0 .05.02.1.07.15.04.05.14.11.31.2l.39.19c.4.2.68.4.83.6.15.22.23.46.23.74 0 .37-.14.68-.41.93-.27.25-.64.37-1.1.37-.61 0-1.1-.24-1.47-.71l.65-.7c.12.14.27.25.43.34.17.09.32.13.45.13s.25-.03.33-.1a.27.27 0 0 0 .13-.23c0-.16-.15-.32-.46-.47l-.36-.18c-.67-.34-1.01-.76-1.01-1.27 0-.33.12-.62.38-.85.26-.24.58-.35.98-.35a1.71 1.71 0 0 1 1.38.69zM.38.1H1V1h.36v.52H1v1.91H.38v-1.9H.07V1h.31V.1zM1.7.06h.61v1.19c.12-.1.24-.18.37-.23a.94.94 0 0 1 .36-.08c.25 0 .45.08.62.25.14.15.21.36.21.64v1.61h-.6V2.37c0-.28-.02-.47-.04-.57a.4.4 0 0 0-.14-.23.39.39 0 0 0-.24-.07.46.46 0 0 0-.32.12.65.65 0 0 0-.19.34c-.02.07-.03.24-.03.5v.98h-.6V.06zM6.91 2.4H4.94c.02.17.1.3.22.41.13.1.29.15.48.15.23 0 .42-.07.59-.23l.52.24a1.28 1.28 0 0 1-1.11.53 1.23 1.23 0 0 1-1.3-1.27A1.25 1.25 0 0 1 5.6.94c.4 0 .7.12.95.37.24.24.36.57.36.97v.12zm-.62-.48a.61.61 0 0 0-.24-.33.7.7 0 0 0-.41-.13.74.74 0 0 0-.45.14.8.8 0 0 0-.23.32H6.3z"/>
      </defs>
      <g 
        id="Juice-bottle" 
        fill="none" 
        fill-rule="evenodd">
        <g 
          id="Juice-bottle-with-label" 
          transform="translate(12 11)">
          <g 
            id="Juice-bottle" 
            filter="url(#filter-1)">
            <g 
              id="Group" 
              transform="translate(0 11.83)">
              <mask 
                id="mask-3" 
                fill="#fff">
                <use xlink:href="#path-2"/>
              </mask>
              <use 
                id="Bottle" 
                fill="#D8D8D8" 
                fill-rule="nonzero" 
                xlink:href="#path-2"/>
              <g 
                id="Orange-Juice" 
                :fill="'url(#'+ uniqueId +')'" 
                fill-rule="nonzero" 
                mask="url(#mask-3)">
                <path 
                  id="Juice-Color" 
                  d="M0 0h115v180H0z" 
                  transform="translate(-3.93 19.72)"/>
              </g>
              <g 
                id="Glass-sheen" 
                fill-rule="nonzero" 
                mask="url(#mask-3)">
                <use 
                  fill="url(#linearGradient-5)" 
                  fill-opacity=".75" 
                  xlink:href="#path-7"/>
                <use 
                  fill="url(#linearGradient-6)" 
                  xlink:href="#path-7" 
                  style="mix-blend-mode:screen"/>
              </g>
            </g>
            <path 
              id="Path-2" 
              fill="#4A4A4A" 
              fill-rule="nonzero" 
              d="M28.79 3.94c0-5.25 48.42-5.25 48.42 0v9.2H28.79v-9.2z"/>
          </g>
          <g 
            id="Bottle-label" 
            transform="translate(15.7 64.4)">
            <path 
              id="Combined-Shape" 
              fill="#FFF" 
              fill-rule="nonzero" 
              d="M13.35 0h50.5c1 0 1.37.12 1.74.35.37.23.65.57.85 1 .2.42.3.85.3 2.02V84.7c0 1.17-.1 1.6-.3 2.02-.2.43-.48.77-.85 1-.37.23-.73.35-1.73.35h-50.5c-1 0-1.37-.12-1.74-.35a2.25 2.25 0 0 1-.85-1c-.2-.42-.3-.85-.3-2.02V3.37c0-1.17.1-1.6.3-2.03.2-.42.48-.76.85-.99.37-.23.73-.35 1.73-.35z"/>
            <g 
              id="Ingredients-list" 
              fill="#D8D8D8" 
              fill-rule="nonzero" 
              transform="translate(22.25 32.86)">
              <path 
                id="Rectangle-4" 
                d="M0 0h31.41v5.26H0z"/>
              <path 
                id="Rectangle-4-Copy" 
                d="M0 9.2h26.17v2.63H0z"/>
              <path 
                id="Rectangle-4-Copy-2" 
                d="M0 15.77h28.79v2.63H0z"/>
              <path 
                id="Rectangle-4-Copy-3" 
                d="M0 22.35h32.72v2.63H0z"/>
              <path 
                id="Rectangle-4-Copy-4" 
                d="M0 28.92h31.41v2.63H0z"/>
              <path 
                id="Rectangle-4-Copy-5" 
                d="M0 35.49h34.02v2.63H0z"/>
              <path 
                id="Rectangle-4-Copy-6" 
                d="M0 42.06h28.79v2.63H0z"/>
            </g>
            <g 
              id="Logo" 
              transform="translate(0 3.94)">
              <g id="Logo-type-Copy-3">
                <g id="Logo-Copy-4">
                  <g 
                    id="Fruit" 
                    transform="translate(2.86 8.7)">
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
                      d="M15.1-4.68C10.37-5.95 7.58.4 9.8 5.64 15.84 4 17.57-2.64 15.1-4.68z" 
                      mask="url(#mask-10)" 
                      style="mix-blend-mode:multiply"/>
                    <path 
                      id="Path-3-Copy-4" 
                      fill="#A9A9A9" 
                      fill-rule="nonzero" 
                      d="M1.75 1.4c-4.08 0-6.05 6.17-2.47 10.24C2.98 7.95 4.46 2.73 1.75 1.4z" 
                      mask="url(#mask-10)" 
                      style="mix-blend-mode:multiply"/>
                    <ellipse 
                      id="Oval-2" 
                      cx="5.56" 
                      cy="3.95" 
                      fill="#FFF" 
                      fill-rule="nonzero" 
                      mask="url(#mask-10)" 
                      rx="1.11" 
                      ry="1.15"/>
                  </g>
                  <path 
                    id="Path-3" 
                    fill="url(#linearGradient-11)" 
                    fill-rule="nonzero" 
                    d="M17.58 3.4c-4.73-1.26-7.51 4.99-5.3 10.17 6.04-1.63 7.76-8.17 5.3-10.18z"/>
                  <path 
                    id="Path-3-Copy-2" 
                    fill="url(#linearGradient-11)" 
                    fill-rule="nonzero" 
                    d="M10.67 1C6.98-.85 1.43 4.12 3.56 9.15c5.66-.98 9.8-6.34 7.11-8.13z" 
                    transform="rotate(8 7.3 4.87)"/>
                  <path 
                    id="Path-3-Copy" 
                    fill="url(#linearGradient-12)" 
                    fill-rule="nonzero" 
                    d="M4.34 9.85c-4.08 0-6.05 6.13-2.48 10.18 3.7-3.67 5.18-8.86 2.48-10.18z"/>
                </g>
                <g 
                  id="Logo/dark" 
                  transform="translate(21.4 3.76)">
                  <mask 
                    id="mask-14" 
                    fill="#fff">
                    <use xlink:href="#path-13"/>
                  </mask>
                  <use 
                    id="the-nimble-press" 
                    fill="#1E1E1E" 
                    xlink:href="#path-13"/>
                </g>
              </g>
            </g>
          </g>
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
    juiceColor: Object,
    juiceName: String,
    bottlePosition: String,
  },
  computed: {
    uniqueId: function() {
      // replace all spaces with _ and add a random number between 1 and 100 on the end
      const juiceComputedId =
        this.juiceName.replace(/\s/g, "_") +
        Math.floor(Math.random() * 100 + 1);
      return juiceComputedId;
    },
    gradientColors: function() {
      return {
        "--top-color": this.juiceColor.top,
        "--bottom-color": this.juiceColor.bottom
      };
    }
  },
  methods: {
    onPan: function(e) {
      // select the svg inside our component not the whole component
      var thisBottle = this.$el.querySelector("svg");

      //set z-index so this bottle is in front all the rest
      this.$el.style.zIndex = "2";

      // tone down the movement input then apply it to the bottle
      var rotate = e.deltaX * 0.06;
      thisBottle.style.transform = "rotate(" + rotate + "deg) translateY(20%) scale(1.1)";
        
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
  svg {
    max-width: 100%;
    transform-origin: 50% 200%;
  }
}
.top-color {
  stop-color: var(--top-color);
}
.bottom-color {
  stop-color: var(--bottom-color);
}
</style>
