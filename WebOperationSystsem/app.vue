<template>
  <div class="container">
    <div v-if="loading.loaded" class="view-container">
      <div class="upbar">
        <upbar />
      </div>
      <div class="board-container">
        <div class="desktop"></div>
      </div>
    </div>
    <div v-if="!loading.loaded" class="loadingloaded">
      <loading />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading: {
        loaded: false,
      },
      desktop: {
        focusApp: '',
      }
    }
  },
  mounted() {
    setTimeout(() => {
      this.loading.loaded = true;
    }, 5000)
  }
}
</script>

<style>
body {
  background-color: gray;
  overflow: hidden;
  top: 0;
  left: 0;
  padding: 0;
  margin: 0;
  width: 100%;
  height: 100%;
}

.view-container {
  color: white;
  font-family: Arial, Helvetica, sans-serif;
  margin-top: 0;
  margin-left: 0;
}
</style>
