<template>
  <i :class="iconClass" :style="iconStyle"></i>
</template>

<script>
export default {
  name: 'IconFont',
  props: {
    // 图标类名，例如: 'icon-innovation'
    iconClass: {
      type: String,
      required: true
    },
    // 图标大小
    size: {
      type: [String, Number],
      default: 'inherit'
    },
    // 图标颜色
    color: {
      type: String,
      default: 'inherit'
    }
  },
  computed: {
    iconStyle() {
      return {
        fontSize: typeof this.size === 'number' ? `${this.size}px` : this.size,
        color: this.color
      }
    }
  }
}
</script>

<style scoped>
/* IconFont 图标样式 */
i {
  display: inline-block;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>