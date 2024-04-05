<template>
  <div>
    <h1>{{ time.upbar_clock }}</h1>
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
      this.time.upbar_clock = new Date().toTimeString().slice(0, 8);
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
.upbar {
  background-color: black;
  height: 40px;
  width: 100%;
  font-size: 0.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  user-select: none;
  -webkit-user-select: none;
}
</style>
