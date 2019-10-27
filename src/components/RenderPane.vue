<template>
  <div class="render-pane" v-bind:style="styles">
    <div class="render-pane-inset">
      <p v-for="(line, index) in this.text.split('\n')" v-bind:key="index">
        {{ line }}
      </p>
    </div>
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
    text: String,
  },
  watch:{
    width: function (val) {
      Vue.set(this, 'styles', { width: `${val}px` })
    },
  },
}
</script>

<style scoped>
.render-pane {
  height: 100%;
  background-color: white;
}

.render-pane-inset {
  width: 95%;
  padding-left: 5%;
}

p {
  text-align: start;
}
</style>
