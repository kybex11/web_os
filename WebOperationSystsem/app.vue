<template>
  <div v-if="!loading.loaded" class="loadingloaded">
    <h1>Loading{{loading.dots}}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading: {
        loaded: false,
        dots: '.'
      }
    }
  },
  methods: {
    updateDots() {
      let dots = this.loading.dots;
      if (dots === '...') {
        dots = '.';
      } else if (dots === '..') {
        dots = '...';
      } else if (dots === '.') {
        dots = '..';
      }
      this.loading.dots = dots;
    }
  },
  mounted() {
    let dotsInterval = setInterval(() => {this.updateDots();}, 200);setTimeout(() => {clearInterval(dotsInterval);this.loading.loaded = true;}, 5000);

  }
}
</script>

<style>
body {background-color:black;overflow:hidden;}
.loadingloaded{user-select:none;-webkit-user-select:none;display: flex;flex-direction: column;text-align: center;align-items: center;justify-content: center;min-height: 100vh;position: relative;}
.loadingloaded h1 {color:white;position: absolute;top: 50%;transform: translateY(-50%);font-family: Arial, Helvetica, sans-serif;}
</style>
