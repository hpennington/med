<template>
  <div
    id="resize-bar"
    @mousedown="onMouseDown"
    @mousemove="onMouseMove"
    @mouseup="onMouseUp"
  >
  </div>
</template>

<script>
export default {
  name: 'ResizeBar',
  data: function () {
    return {
      mouseDown: false,
    }
  },
  props: {
    resizeDrag: Function
  },
  created: function () {
    window.addEventListener('mouseup', this.onMouseUp)
    window.addEventListener('mousemove', this.onMouseMove)
  },
  methods: {
    onMouseDown: function () {
      this.$set(this, 'mouseDown', true)
    },
    onMouseMove: function (e) {
      if (this.mouseDown === true) {
        this.onDrag(e.clientX)
      }
    },
    onMouseUp: function () {
      this.$set(this, 'mouseDown', false)
    },
    onDrag: function (x) {
      const resizeBar = document.getElementById('resize-bar')
      const barWidth = resizeBar.getBoundingClientRect().width
      const app = document.getElementById('app')
      const appWidth = app.getBoundingClientRect().width

      if (x >= 0 && x <= appWidth - barWidth) {
        resizeBar.style.left = `${x}px`
        this.resizeDrag(x)
      }
    },
  },
}
</script>

<style scoped>
#resize-bar {
  --bar-width: 6px;
  position: absolute;
  left: calc(50% - calc(var(--bar-width) / 2));
  height: 100%;
  width: var(--bar-width);
  background-color: lightgray;
  cursor: col-resize;
}
#resize-bar:hover {
  background-color: darkgray;
}
</style>
