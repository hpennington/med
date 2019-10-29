<script>
export default {
  name: 'RenderLine',
  props: {
    text: String,
    level: Number,
  },
  render: function (createElement) {
    if (this.text.startsWith('######') === true) {
      return createElement(
        'h6',
        this.text.substring(6, this.text.length)
      )
    } else if (this.text.startsWith('#####') === true) {
      return createElement(
        'h5',
        this.text.substring(5, this.text.length)
      )
    } else if (this.text.startsWith('####') === true) {
      return createElement(
        'h4',
        this.text.substring(4, this.text.length)
      )
    } else if (this.text.startsWith('###') === true) {
      return createElement(
        'h3',
        this.text.substring(3, this.text.length)
      )
    } else if (this.text.startsWith('##') === true) {
      return createElement(
        'h2',
        this.text.substring(2, this.text.length)
      )
    } else if (this.text.startsWith('#') === true) {
      return createElement(
        'h1',
        this.text.substring(1, this.text.length)
      )
    } else {
      return createElement(
        'p',
        this.$slots.default
      )
    }
  },
}
</script>

<style scoped>
</style>
