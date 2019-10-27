<template>
  <div class="edit-pane" v-bind:style="styles">
    Editor
  </div>
</template>

<script>
import Vue from 'vue'

export default {
  name: 'EditPane',
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
.edit-pane {
  height: 100%;
  background-color: gray;
}
</style>
