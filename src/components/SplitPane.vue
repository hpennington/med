<template>
  <div id="split-pane-container">
    <EditPane v-bind:width="editWidth" :onTextChange="onTextChange" />
    <ResizeBar :resizeDrag="resizeDrag" />
    <RenderPane v-bind:width="renderWidth" :text="text" />
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
    const appWidth = document.getElementById('app').getBoundingClientRect().width
    return {
      editWidth: appWidth / 2,
      renderWidth: appWidth / 2,
      text: '',
    }
  },
  methods: {
    resizeDrag: function (x) {
      this.$set(this, 'editWidth', x)

      const appWidth = document.getElementById('app').getBoundingClientRect().width
      this.$set(this, 'renderWidth', appWidth - x)
    },
    onTextChange(val) {
      this.$set(this, 'text', val)
    },
  },
  watch: {
    text: function (val) {
      console.log(val)
      console.log('watching on text in split pane')
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
