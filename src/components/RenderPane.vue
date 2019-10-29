<template>
  <div class="render-pane" v-bind:style="styles">
    <div class="render-pane-inset">
      <RenderLine
        id="markdown-container"
        v-for="(line, index) in this.markdown"
        v-bind:key="index"
        :level="0"
        :text="line"
      >
        {{ line }}
      </RenderLine>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import RenderLine from './RenderLine.vue'

export default {
  name: 'RenderPane',
  components: {
    RenderLine,
  },
  data: function () {
    return {
      styles: { width: `${this.width}px` }
    }
  },
  props: {
    width: Number,
    markdown: Array,
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
  overflow-y: scroll;
}

.render-pane-inset {
  width: 95%;
  padding-left: 5%;
}

#markdown-container {
  text-align: start;
}

p {
  text-align: start;
}
</style>
