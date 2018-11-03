<template>
  <div class="footer">
    <router-link :to="{ name:'cart', params: { cartContents }}">
      <div class="cart-icon">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="112" height="84" viewBox="0 0 112 84">
          <title>
            shopping cart
          </title>
          <defs>
            <filter id="a" width="170.5%" height="218.6%" x="-35.3%" y="-53.8%" filterUnits="objectBoundingBox">
              <feOffset dy="5" in="SourceAlpha" result="shadowOffsetOuter1"/>
              <feGaussianBlur in="shadowOffsetOuter1" result="shadowBlurOuter1" stdDeviation="5"/>
              <feColorMatrix in="shadowBlurOuter1" result="shadowMatrixOuter1" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.2 0"/>
              <feMerge>
                <feMergeNode in="shadowMatrixOuter1"/>
                <feMergeNode in="SourceGraphic"/>
              </feMerge>
            </filter>
            <ellipse id="c" cx="22.1" cy="52.3" rx="8.1" ry="8.1"/>
            <filter id="b" width="223.2%" height="223.4%" x="-61.6%" y="-49.4%" filterUnits="objectBoundingBox">
              <feMorphology in="SourceAlpha" operator="dilate" radius="3" result="shadowSpreadOuter1"/>
              <feOffset dy="2" in="shadowSpreadOuter1" result="shadowOffsetOuter1"/>
              <feGaussianBlur in="shadowOffsetOuter1" result="shadowBlurOuter1" stdDeviation="2"/>
              <feComposite in="shadowBlurOuter1" in2="SourceAlpha" operator="out" result="shadowBlurOuter1"/>
              <feColorMatrix in="shadowBlurOuter1" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.2 0"/>
            </filter>
            <ellipse id="e" cx="79.8" cy="52.3" rx="8.1" ry="8.1"/>
            <filter id="d" width="223.2%" height="223.4%" x="-61.6%" y="-49.4%" filterUnits="objectBoundingBox">
              <feMorphology in="SourceAlpha" operator="dilate" radius="3" result="shadowSpreadOuter1"/>
              <feOffset dy="2" in="shadowSpreadOuter1" result="shadowOffsetOuter1"/>
              <feGaussianBlur in="shadowOffsetOuter1" result="shadowBlurOuter1" stdDeviation="2"/>
              <feComposite in="shadowBlurOuter1" in2="SourceAlpha" operator="out" result="shadowBlurOuter1"/>
              <feColorMatrix in="shadowBlurOuter1" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.2 0"/>
            </filter>
          </defs>
          <g class="cart-inner" fill="none" fill-rule="evenodd" filter="url(#a)" transform="translate(10.3 12)">
            <path stroke="#979797" stroke-width="6" d="M22.9 9.6a3 3 0 0 0-3 3.8l5.2 20.4a3 3 0 0 0 3 2.2h46.7a3 3 0 0 0 2.7-1.6L87.7 14A3 3 0 0 0 85 9.6H22.9z"/>
            <g fill="#979797" fill-rule="nonzero">
              <path d="M20.5 14.5H86v3.4H20.5zM22.2 21.3h61.4v3.4H22.2zM23.9 28h56.3v3.5H23.9z"/>
              <path d="M29.9 35.7V9.3h3.4v26.4zM21.3 26.3v-17h3.4v17zM38.4 35.7V9.3h3.4v26.4zM47 35.8V9.4h3.3v26.4zM55.4 35.7V9.4h3.4v26.3zM64 35.7V9.3h3.4v26.4zM72.5 35.7V9.3h3.4v26.4zM81 26.4v-17h3.4v17z"/>
            </g>
            <path stroke="#979797" stroke-linecap="round" stroke-linejoin="round" stroke-width="6" d="M0 0h13.7c1 0 1.8.7 2 1.6L23 38l-3.5 14.3H79"/>
            <g fill-rule="nonzero">
              <use fill="#000" filter="url(#b)" xlink:href="#c"/>
              <use fill="#9B9B9B" stroke="#4A4A4A" stroke-width="6" xlink:href="#c"/>
            </g>
            <g fill-rule="nonzero">
              <use fill="#000" filter="url(#d)" xlink:href="#e"/>
              <use fill="#9B9B9B" stroke="#4A4A4A" stroke-width="6" xlink:href="#e"/>
            </g>
          </g>
        </svg>
        <span class="cart-counter" v-if="cartHasItems">{{this.cartContents.length}}</span>
      </div>
    </router-link>
    <button class="add-to-cart btn"
      v-on:click="addToCart"
      v-hammer:press="() => addToCart">
      Add to Cart
    </button>
    
  </div>
</template>

<script>
import anime from "animejs";

export default {
  name: "Footer",
  props: {
    cartContents: Array,
    selectedJuice: Object
  },
  data () {
    return {
      cartContains: () => this.cartContents
    }
  },
  computed: {
    cartHasItems: function() {
      return this.cartContents.length >= 1;
    }

  },
  watch: {

  },
  methods: {
    addToCart: function() {
      setTimeout( () => this.cartContents.push(this.selectedJuice), 500);

      let selectedJuice = document.querySelector('.juice-bottle.selected svg');
      let cartInner = document.querySelector('.footer .cart-inner');

      var flipAnimTo = function(element, to){
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
        }
        // Set the transform origin point so it works with the calculated co-ordinates
        element.style.transformOrigin = 'left top';
        element.style.zIndex = '100';
        
        // Apply transform to sync the from class back to the 'to' classes position
        // element.style.transform = 'translateX(' + invertedRect.left + 'px) translateY(' + invertedRect.top + 'px) scaleX(' + invertedRect.width + ') scaleY(' + invertedRect.height + ')';

        const juiceToCart = anime.timeline()
        .add({
          targets: element,
          translateY: [
            { value: 30, duration: 200, easing: 'easeOutCubic' },
            { value: invertedRect.top, duration: 200, easing: [0.15, 0, 0.2, 0] }
          ],
          translateX: [
            { value: 0, duration: 200, easing: 'easeOutCubic' },
            { value: invertedRect.left, duration: 200, easing: [0.15, 0, 0.2, 0] }
          ],
          rotate: [
            { value: -20, duration: 200, easing: 'easeOutCubic'},
            { value: 0, duration: 50, easing: 'easeOutSine'},
          ],
          scaleX: [
            { value: 1.2, duration: 200, easing: 'easeOutCubic'},
            { value: 0.2, duration: 200, easing: 'easeOutSine'},
          ],
          scaleY: [
            { value: 1.2, duration: 200, easing: 'easeOutCubic'},
            { value: 0.2, duration: 200, easing: 'easeOutSine'},
          ],
          complete: function() {
            element.style.transformOrigin = '50%';
            element.style.opacity = '0';
            element.style.transform = 'translateX(0px) translateY(0px)';
          },
        })
        .add({
          targets: '.cart-icon svg',
          translateX: [
            { value: -10, duration: 50, easing: 'easeOutCubic' },
            { value: 0, duration: 500 }
          ],
          translateY: [
            { value: 30, duration: 50, easing: 'easeOutCubic' },
            { value: 0, duration: 500 }
          ],
        })
        .add({
          targets: element,
          scale: [0.9, 1],
          opacity: 1,
          duration: 500,
          offset: '-=200',
          complete: function() {
            // remove left over inline styles so the swipe transformations work correctly
            element.style.cssText= "";
          }
        })

      };
      flipAnimTo(selectedJuice, cartInner);
    }
  }
};
</script>

<style scoped lang="scss">
@import "../assets/_variables.scss";

.footer {
  background-color: $color_brand_purple;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-around;
  padding: 1rem;
}

.cart-icon {
  position: relative;
  svg {
    height: 40px;
  }
}
.cart-counter {
  position: absolute;
  top: -10px;
  right: 15px;
  background-color: $color_brand_turquoise;
  color: white;
  font-weight: 800;
  padding-top: 6px;
  height: 30px;
  width: 30px;
  border-radius: 100px;
  animation: scaleIn 0.2s ease-out;
}

@keyframes scaleIn {
  0%{transform: scale(0.5); opacity: 0}
  90%{transform: scale(1.1); opacity: 1}
  100%{transform: scale(1); opacity: 1}
}

</style>
