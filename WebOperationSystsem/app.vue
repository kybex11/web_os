<template>
  <div class="container">
    <div v-if="loading.loaded" class="view-container">
      <div class="upbar">
        <h1>{{time.upbar_clock}}</h1>
      </div>
      <div class="board-container">
        <div class="desktop"></div>
      </div>
    </div>
    <div v-if="!loading.loaded" class="loadingloaded">
      <h1>Loading{{loading.dots}}</h1>
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
      },
      time: {
        upbar_clock: '00:00:00'
      }
    }
  },
  methods: {
    updateUpbarClock() {
      this.time.upbar_clock = new Date().toTimeString().slice(0,8);
    },
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
    this.updateUpbarClock();
    setInterval(() => {
      this.updateUpbarClock();
    }, 1000)
  }
}
</script>

<style>
body {background-color:gray;overflow:hidden;top:0;left:0;padding:0;margin:0;width:100%;height:100%;}
.upbar {background-color:black;height:40px;width:100%;font-size: 0.5rem;display:flex;justify-content:center;align-items:center;user-select:none;-webkit-user-select:none;}
.loadingloaded{user-select:none;-webkit-user-select:none;display: flex;flex-direction: column;text-align: center;align-items: center;justify-content: center;min-height: 100vh;position: relative;}
.loadingloaded h1 {color:white;position: absolute;top: 50%;transform: translateY(-50%);font-family: Arial, Helvetica, sans-serif;}
.view-container {color: white;font-family: Arial, Helvetica, sans-serif;margin-top:0;margin-left:0;}
</style>
