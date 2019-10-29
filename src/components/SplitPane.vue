<template>
  <div id="split-pane-container">
    <EditPane :width="editWidth" :onTextChange="onTextChange" />
    <ResizeBar :resizeDrag="resizeDrag" />
    <RenderPane :width="renderWidth" :markdown="markdown" />
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
  computed: {
    markdown: function () {
      return this.text.split('\n')
    }
  },
  methods: {
    resizeDrag: function (x) {
      this.editWidth = x

      const appWidth = document.getElementById('app').getBoundingClientRect().width
      this.renderWidth = appWidth - x
    },
    onTextChange(val) {
      this.text = val
    },
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
