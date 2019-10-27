<template>
  <div class="render-pane" v-bind:style="styles">
    Render
  </div>
</template>

<script>
import Vue from 'vue'

export default {
  name: 'RenderPane',
  data: function () {
    return {
      styles: { width: `${this.width}px` }
    }
  },
  props: {
    width: Number,
  },
  watch:{
    width: function (val) {
      Vue.set(this, 'styles', { width: `${val}px` })
    }
  },
}
</script>

<style scoped>
.render-pane {
  height: 100%;
  background-color: white;
}
</style>
