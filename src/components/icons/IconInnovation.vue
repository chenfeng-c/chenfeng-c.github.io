<template>
  <IconFont iconClass="icon-innovation" :size="size" :color="color" />
</template>

<script>
import IconFont from '../IconFont.vue'

export default {
  name: 'IconInnovation',
  components: {
    IconFont
  },
  props: {
    size: {
      type: [String, Number],
      default: 40
    },
    color: {
      type: String,
      default: '#0066CC'
    }
  }
}
</script>