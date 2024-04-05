<template>
  <div class="container">
    <div v-if="loading.loaded" class="view-container">
      <div class="upbar">
        <upbar/>
      </div>
      <div class="board-container">
        <div class="desktop"></div>
      </div>
    </div>
    <div v-if="!loading.loaded" class="loadingloaded">
      <h1>Loading{{loading.dots}}</h1>
      <!--<h2>Please don't turn off your PC</h2>-->
    </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      loading: {
        loaded: false,
        dots: '.'
      },
      desktop: {
        focusApp: '',
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
body {background-color:gray;overflow:hidden;top:0;left:0;padding:0;margin:0;width:100%;height:100%;}
.loadingloaded{user-select:none;-webkit-user-select:none;display: flex;flex-direction: column;text-align: center;align-items: center;justify-content: center;min-height: 100vh;position: relative;}
.loadingloaded h1 {font-size: 4em; text-shadow: 0 0 0.2em rgba(0, 0, 0, 0.8), 0.05em 0.05em 0.1em rgba(0, 0, 0, 0.5);transform:perspective(500px) rotateX(10deg) rotateY(-15deg);transform-style: preserve-3d; color:white;position: relative;top: 50%;transform: translateY(-50%);font-family: Arial, Helvetica, sans-serif;}
.loadingloaded h1:before {content:"";position:absolute;top: -10px; left: -10px; right: -10px; bottom:-10px;border: 5px solid "#663399";z-index:-1;}
.view-container {color: white;font-family: Arial, Helvetica, sans-serif;margin-top:0;margin-left:0;}
</style>
