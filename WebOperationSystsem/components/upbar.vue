<template>
  <div>
    <h1>{{time.upbar_clock}}</h1>
  </div>
</template>
<script>
export default {
  data() {
    return {
      time: {
        upbar_clock: '00:00:00'
      }
    }
  },
  methods: {
    updateUpbarClock() {
      this.time.upbar_clock = new Date().toTimeString().slice(0,8);
    },
  },
  mounted() {
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
</style>
