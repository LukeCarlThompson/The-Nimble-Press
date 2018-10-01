<template>
    <svg :class="['juice-bottle', bottlePosition, juiceColor]"
     xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="130" height="200" viewBox="0 0 130 250">
      <title>
        Juice bottle color fill
      </title>
      <defs>
        <filter id="filter-1" width="130.2%" height="115.3%" x="-15.1%" y="-5.5%" filterUnits="objectBoundingBox">
          <feOffset dy="5" in="SourceAlpha" result="shadowOffsetOuter1"/>
          <feGaussianBlur in="shadowOffsetOuter1" result="shadowBlurOuter1" stdDeviation="5"/>
          <feColorMatrix in="shadowBlurOuter1" result="shadowMatrixOuter1" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.2 0"/>
          <feMerge>
            <feMergeNode in="shadowMatrixOuter1"/>
            <feMergeNode in="SourceGraphic"/>
          </feMerge>
        </filter>
        <path id="path-2" d="M38.67 0C38.67 25.92 0 14.4 0 47.53v156.99c0 14.4 116 14.4 116 0v-157C116 14.4 77.33 25.93 77.33 0H38.67z"/>
        <linearGradient id="linearGradient-4" x1="50%" x2="50%" y1="0%" y2="100%">
          <stop offset="0%" stop-color="#C4C4C4"/>
          <stop offset="100%" stop-color="#616161"/>
        </linearGradient>
        <linearGradient id="linearGradient-5" x1="0%" x2="79.82%" y1="40.97%" y2="40.97%">
          <stop offset="0%" stop-color="#55DFFF" stop-opacity="0"/>
          <stop offset="29.23%" stop-color="#FFF" stop-opacity=".55"/>
          <stop offset="100%" stop-color="#77DBFF" stop-opacity="0"/>
        </linearGradient>
        <linearGradient id="linearGradient-6" x1="39.91%" x2="39.91%" y1="5.86%" y2="24.04%">
          <stop offset="0%" stop-color="#FFF" stop-opacity="0"/>
          <stop offset="29.23%" stop-color="#FFF" stop-opacity=".55"/>
          <stop offset="100%" stop-color="#FFF" stop-opacity="0"/>
        </linearGradient>
        <path id="path-7" d="M-4.3-2.88h126.02v221.8H-4.3z"/>
        <radialGradient id="radialGradient-8" cx="29.05%" cy="18.64%" r="88.46%" fx="29.05%" fy="18.64%" gradientTransform="matrix(.47636 .82835 -.87925 .44878 .32 -.14)">
          <stop offset="0%" stop-color="#CEAAF4"/>
          <stop offset="50.84%" stop-color="#9C75C5"/>
          <stop offset="100%" stop-color="#5C3586"/>
        </radialGradient>
        <ellipse id="path-9" cx="8.97" cy="9.52" rx="8.97" ry="9.52"/>
        <linearGradient id="linearGradient-11" x1="50%" x2="62.81%" y1="0%" y2="67.01%">
          <stop offset="0%" stop-color="#9FE3DA"/>
          <stop offset="56.36%" stop-color="#66C2B3"/>
          <stop offset="100%" stop-color="#45AA99"/>
        </linearGradient>
        <linearGradient id="linearGradient-12" x1="50%" x2="50%" y1="0%" y2="79.54%">
          <stop offset="0%" stop-color="#9FE3DA"/>
          <stop offset="56.36%" stop-color="#66C2B3"/>
          <stop offset="100%" stop-color="#45AA99"/>
        </linearGradient>
        <path id="path-13" d="M.57 7.51H1.7v.47c.26-.22.5-.37.7-.46.21-.08.43-.13.64-.13.45 0 .83.16 1.15.48.26.28.4.68.4 1.2v3.06H3.45V10.1c0-.56-.02-.92-.07-1.1a.75.75 0 0 0-.26-.42.7.7 0 0 0-.44-.14.83.83 0 0 0-.6.24c-.16.15-.27.37-.34.65-.03.14-.05.45-.05.94v1.85H.57V7.5zm5.55-1.9a.74.74 0 0 1 .73.76c0 .2-.07.38-.21.53a.68.68 0 0 1-.5.21.75.75 0 0 1-.73-.76c-.01-.2.06-.38.2-.52a.69.69 0 0 1 .51-.22zm-.57 1.9H6.7v4.62H5.55V7.5zm2.16 0h1.14v.53a1.85 1.85 0 0 1 1.42-.65 1.42 1.42 0 0 1 1.31.84 1.77 1.77 0 0 1 2.37-.6c.24.15.42.35.52.6.1.24.16.64.16 1.2v2.7H13.5V9.79c0-.53-.06-.88-.2-1.07-.12-.18-.3-.27-.56-.27-.2 0-.37.05-.52.17a1 1 0 0 0-.35.46c-.07.2-.11.52-.11.97v2.08h-1.14V9.89c0-.41-.03-.7-.1-.9a.81.81 0 0 0-.26-.4.7.7 0 0 0-.43-.14.84.84 0 0 0-.51.17c-.16.11-.27.27-.35.48-.08.2-.11.53-.11.98v2.05H7.7V7.5zm9.13-1.78v2.3a1.88 1.88 0 0 1 1.43-.63c.59 0 1.09.22 1.5.68.41.45.62 1.04.62 1.75 0 .69-.21 1.26-.64 1.72a2 2 0 0 1-2.24.56c-.23-.1-.45-.25-.67-.47v.49H15.7v-6.4h1.13zm1.19 2.73c-.36 0-.65.13-.89.38-.23.25-.35.57-.35.97 0 .41.12.74.35 1 .24.25.53.38.89.38.35 0 .64-.13.87-.39.24-.26.36-.58.36-.98s-.12-.72-.35-.98a1.14 1.14 0 0 0-.88-.38zm3.18-2.73h1.13v6.4h-1.13v-6.4zm6.68 4.43h-3.64c.05.32.2.59.42.78.23.2.52.29.88.29.42 0 .79-.15 1.09-.45l.96.45a2.27 2.27 0 0 1-2.04 1.02 2.31 2.31 0 0 1-2.4-2.4c0-.7.22-1.3.66-1.76.45-.46 1-.7 1.67-.7.72 0 1.3.24 1.74.7.45.47.67 1.08.67 1.85v.22zm-1.13-.92a1.16 1.16 0 0 0-.45-.62 1.26 1.26 0 0 0-.76-.25c-.32 0-.6.1-.83.28-.15.1-.3.3-.42.6h2.46zM1.7 14.57v.51a1.88 1.88 0 0 1 1.43-.63c.59 0 1.09.23 1.5.69.41.45.62 1.04.62 1.75 0 .69-.21 1.26-.64 1.72a2 2 0 0 1-2.24.56c-.23-.1-.45-.25-.67-.47v2.18H.57v-6.3H1.7zm1.2.95c-.37 0-.66.13-.9.38-.23.25-.35.57-.35.97 0 .41.12.74.35 1 .24.25.53.38.9.38.34 0 .63-.13.87-.39.23-.26.35-.58.35-.98s-.12-.72-.35-.98a1.14 1.14 0 0 0-.88-.38zm3.02-.95h.97v.58c.11-.22.25-.4.42-.52a1 1 0 0 1 1.04-.06l-.35 1a.77.77 0 0 0-.33-.1c-.18 0-.32.1-.45.33-.12.22-.18.65-.18 1.3V19.19H5.93v-4.62zm7.52 2.65H9.79c.06.32.2.59.43.78.22.2.52.29.87.29.42 0 .79-.15 1.1-.45l.95.45a2.27 2.27 0 0 1-2.04 1.02 2.31 2.31 0 0 1-2.4-2.4c0-.7.22-1.3.66-1.76.45-.46 1-.7 1.68-.7.7 0 1.29.24 1.73.7.45.47.67 1.08.67 1.85v.22zm-1.14-.92a1.16 1.16 0 0 0-.44-.62 1.26 1.26 0 0 0-.77-.25c-.32 0-.6.1-.83.28-.15.1-.29.3-.42.6h2.46zm4.82-1.08l-.7.72c-.29-.3-.55-.44-.78-.44a.48.48 0 0 0-.3.09.25.25 0 0 0-.04.37c.05.06.16.13.34.22l.42.2c.43.23.74.45.9.68.16.23.24.5.24.81 0 .41-.14.75-.44 1.03-.3.27-.69.4-1.18.4-.66 0-1.19-.25-1.58-.78l.7-.78c.13.16.28.29.46.39.18.1.34.14.48.14.15 0 .27-.03.36-.1.1-.08.14-.17.14-.26 0-.18-.17-.35-.5-.52l-.38-.2c-.73-.38-1.1-.85-1.1-1.41 0-.37.14-.68.42-.94.27-.26.62-.39 1.05-.39a1.8 1.8 0 0 1 1.5.77zm3.74 0l-.7.72c-.28-.3-.54-.44-.78-.44a.48.48 0 0 0-.3.09.25.25 0 0 0-.03.37c.04.06.15.13.33.22l.42.2c.44.23.74.45.9.68.16.23.25.5.25.81 0 .41-.15.75-.45 1.03-.3.27-.69.4-1.18.4-.66 0-1.19-.25-1.58-.78l.7-.78c.13.16.29.29.46.39.18.1.34.14.48.14.15 0 .27-.03.36-.1.1-.08.14-.17.14-.26 0-.18-.17-.35-.5-.52l-.38-.2c-.73-.38-1.1-.85-1.1-1.41 0-.37.14-.68.42-.94.27-.26.63-.39 1.06-.39a1.8 1.8 0 0 1 1.48.77zM.41.12h.66v.99h.4v.58h-.4V3.8H.41V1.7H.08v-.58H.4v-1zM1.82.07h.66v1.31c.13-.11.26-.2.4-.26a.99.99 0 0 1 .39-.08c.26 0 .48.1.66.28.15.16.23.4.23.7V3.8h-.65V2.62c0-.31-.02-.52-.05-.63a.44.44 0 0 0-.14-.25.41.41 0 0 0-.26-.08.49.49 0 0 0-.35.13c-.1.1-.16.22-.2.38-.02.08-.03.26-.03.55V3.8h-.66V.07zm5.62 2.58H5.32c.03.2.1.34.24.46.13.11.3.17.51.17.25 0 .46-.1.64-.27l.56.27a1.32 1.32 0 0 1-1.2.6 1.35 1.35 0 0 1-1.4-1.41c0-.41.14-.75.4-1.02.25-.27.58-.41.97-.41.42 0 .75.14 1.01.4.26.28.4.64.4 1.08v.13zm-.66-.53a.68.68 0 0 0-.26-.37.74.74 0 0 0-.45-.14.78.78 0 0 0-.48.16.88.88 0 0 0-.25.35h1.44z"/>
      </defs>
      <g id="Juice-bottle-color-fill" fill="none" fill-rule="evenodd">
        <g id="Juice-bottle-Copy-10" transform="translate(7 1)">
          <g id="Juice-bottle" filter="url(#filter-1)">
            <g id="Group" transform="translate(0 12.96)">
              <mask id="mask-3" fill="#fff">
                <use xlink:href="#path-2"/>
              </mask>
              <use id="Bottle" fill="#D8D8D8" fill-rule="nonzero" xlink:href="#path-2"/>
              <path id="Juice-Color" class="juice-color-fill" fill-rule="nonzero" d="M-4.3 21.6h126.02v197.31H-4.3z" mask="url(#mask-3)"/>
              <path id="Juice-Luma" fill="url(#linearGradient-4)" fill-rule="nonzero" d="M-4.3 21.6h126.02v197.31H-4.3z" mask="url(#mask-3)" style="mix-blend-mode:luminosity"/>
              <g id="Glass-sheen" fill-rule="nonzero" mask="url(#mask-3)">
                <use fill="url(#linearGradient-5)" fill-opacity=".75" xlink:href="#path-7"/>
                <use fill="url(#linearGradient-6)" style="mix-blend-mode:screen" xlink:href="#path-7"/>
              </g>
            </g>
            <path id="Path-2" fill="#4A4A4A" fill-rule="nonzero" d="M31.5 4.32c0-5.76 53-5.76 53 0V14.4h-53V4.32z"/>
          </g>
          <g id="Bottle-label" transform="translate(17 71)">
            <path id="Combined-Shape" fill="#FFF" fill-rule="nonzero" d="M14.55 0h55.02c1.1 0 1.5.13 1.9.39.4.25.7.62.92 1.1.21.46.33.93.33 2.22v89.55c0 1.3-.12 1.76-.33 2.23-.21.48-.53.85-.93 1.1-.4.25-.8.39-1.89.39H14.55c-1.1 0-1.49-.14-1.89-.4-.4-.24-.71-.61-.93-1.09a4.85 4.85 0 0 1-.32-2.23V3.71c0-1.29.11-1.76.32-2.23.22-.47.53-.84.93-1.1.4-.25.8-.38 1.9-.38z"/>
            <g id="Ingredients-list" fill="#D8D8D8" fill-rule="nonzero" transform="translate(24.24 36.18)">
              <path id="Rectangle-4" d="M0 0h34.22v5.79H0z"/>
              <path id="Rectangle-4-Copy" d="M0 10.13h28.52v2.89H0z"/>
              <path id="Rectangle-4-Copy-2" d="M0 17.37h31.37v2.89H0z"/>
              <path id="Rectangle-4-Copy-3" d="M0 24.61h35.65v2.89H0z"/>
              <path id="Rectangle-4-Copy-4" d="M0 31.84h34.22v2.89H0z"/>
              <path id="Rectangle-4-Copy-5" d="M0 39.08h37.07v2.89H0z"/>
              <path id="Rectangle-4-Copy-6" d="M0 46.32h31.37v2.89H0z"/>
            </g>
            <g id="Logo" transform="translate(0 4.34)">
              <g id="Logo-type-Copy-3">
                <g id="Logo-Copy-4">
                  <g id="Fruit" transform="translate(3.1 9.7)">
                    <mask id="mask-10" fill="#fff">
                      <use xlink:href="#path-9"/>
                    </mask>
                    <g id="Oval" fill-rule="nonzero">
                      <use fill="url(#radialGradient-8)" xlink:href="#path-9"/>
                      <use fill="#F56F23" style="mix-blend-mode:color" xlink:href="#path-9"/>
                    </g>
                    <path id="Path-3-Copy-3" fill="#A9A9A9" fill-rule="nonzero" d="M16.39-5.22C11.25-6.64 8.22.43 10.63 6.3c6.56-1.85 8.44-9.23 5.76-11.5z" mask="url(#mask-10)" style="mix-blend-mode:multiply"/>
                    <path id="Path-3-Copy-4" fill="#A9A9A9" fill-rule="nonzero" d="M1.9 1.56C-2.53 1.56-4.67 8.44-.79 13c4.02-4.12 5.63-9.95 2.7-11.43z" mask="url(#mask-10)" style="mix-blend-mode:multiply"/>
                    <ellipse id="Oval-2" cx="6.03" cy="4.4" fill="#FFF" fill-rule="nonzero" mask="url(#mask-10)" rx="1.21" ry="1.28"/>
                  </g>
                  <path id="Path-3" fill="url(#linearGradient-11)" fill-rule="nonzero" d="M19.08 3.78c-5.13-1.4-8.15 5.58-5.75 11.36 6.55-1.83 8.42-9.11 5.75-11.36z"/>
                  <path id="Path-3-Copy-2" fill="url(#linearGradient-11)" fill-rule="nonzero" d="M11.58 1.12C7.58-.96 1.55 4.6 3.86 10.2c6.15-1.08 10.63-7.07 7.72-9.07z" transform="rotate(8 7.92 5.43)"/>
                  <path id="Path-3-Copy" fill="url(#linearGradient-12)" fill-rule="nonzero" d="M4.7 10.99c-4.42 0-6.55 6.83-2.68 11.35 4.01-4.1 5.62-9.88 2.69-11.35z"/>
                </g>
                <g id="Logo/dark" transform="translate(23.21 4.2)">
                  <mask id="mask-14" fill="#fff">
                    <use xlink:href="#path-13"/>
                  </mask>
                  <use id="the-nimble-press" fill="#1E1E1E" xlink:href="#path-13"/>
                </g>
              </g>
            </g>
          </g>
        </g>
      </g>
    </svg>

</template>

<script>
export default {
  name: "JuiceBottle",
  // data() {
  //   return {
  //     thisJuiceColor: {
  //       top: "#F6D663",
  //       bottom: "#F77C1C"
  //     }
  //   };
  // },
  props: {
    juiceColor: String,
    bottlePosition: '',
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.orange {
  .juice-color-fill {
    fill: #FF8B00;
  }
}

.red {
  .juice-color-fill {
    fill: #B40000;
  }
}

.purple {
  .juice-color-fill {
    fill: #473E9D;
  }
}

.green {
  .juice-color-fill {
    fill: #359041;
  }
}

</style>

