<template>
  <div class="edit-pane" v-bind:style="styles">
    <textarea id="edit-text-area" v-model="text">
    </textarea>
  </div>
</template>

<script>
import Vue from 'vue'

export default {
  name: 'EditPane',
  data: function () {
    return {
      styles: { width: `${this.width}px` },
      text: '',
    }
  },
  props: {
    width: Number,
    onTextChange: Function,
  },
  watch:{
    width: function (val) {
      Vue.set(this, 'styles', { width: `${val}px` })
    },
    text: function (val) {
      console.log(`watch text: ${val}`)
      this.onTextChange(val)
    },
  },
  methods: {
  },
}
</script>

<style scoped>
.edit-pane {
  height: 100%;
  background-color: gray;
  display: flex;
}
#edit-text-area {
  background-color: inherit;
  width: 95%;
  height: 100%;
  font-size: 1em;
  border: none;
  margin: 5%;
  outline: none;
}
</style>
