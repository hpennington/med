<template>
  <div id="split-pane-container">
    <EditPane v-bind:width="editWidth" />
    <ResizeBar :resizeDrag="resizeDrag" />
    <RenderPane v-bind:width="renderWidth" />
  </div>
</template>

<script>
import ResizeBar from './ResizeBar.vue'
import EditPane from './EditPane.vue'
import RenderPane from './RenderPane.vue'

export default {
  name: 'SplitPane',
  components: {
    ResizeBar,
    EditPane,
    RenderPane,
  },
  data: function () {
    return {
      editWidth: 100,
      renderWidth: 100,
    }
  },
  methods: {
    resizeDrag: function (x) {
      this.$set(this, 'editWidth', x)

      const appWidth = document.getElementById('app').getBoundingClientRect().width
      this.$set(this, 'renderWidth', appWidth - x)
    }
  },
}
</script>

<style scoped>
#split-pane-container {
  height: 100%;
  width: 100%;
  display: flex;
}
</style>
