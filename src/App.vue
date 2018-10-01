<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">
      <div class="header-logo dark"></div>
      </router-link>
      <router-link to="/about" class="account-link">
        <svg xmlns="http://www.w3.org/2000/svg" width="30" height="30" viewBox="0 0 48 48">
          <g class="nc-icon-wrapper" fill="#000000">
              <path d="M24 11.8c2.32 0 4.2 1.88 4.2 4.2s-1.88 4.2-4.2 4.2-4.2-1.88-4.2-4.2 1.88-4.2 4.2-4.2m0 18c5.95 0 12.2 2.91 12.2 4.2v2.2H11.8V34c0-1.29 6.25-4.2 12.2-4.2M24 8c-4.42 0-8 3.58-8 8 0 4.41 3.58 8 8 8s8-3.59 8-8c0-4.42-3.58-8-8-8zm0 18c-5.33 0-16 2.67-16 8v6h32v-6c0-5.33-10.67-8-16-8z"></path>
          </g>
        </svg>
      </router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  
}
</script>


<style lang="scss">

@import 'assets/modern-normalize';

body {
  background: linear-gradient(to bottom, white, #C6FFF2);
  min-height: 100vh;
  margin: 0;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 10px;
  display: flex;
  justify-content: center;
  .header-logo {
    height: 70px;
    width: 150px;
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center center;
    &.dark {
      background-image: url('./assets/logo.min.svg');
    }
  }
  .account-link {
    position: absolute;
    right: 20px;
    top: 20px;
    transition: transform 0.3s ease-out;
    &:hover, &:active {
      transform: scale(1.2);
    }
  }
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
