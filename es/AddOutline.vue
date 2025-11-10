<template>
  <svg
    :width="size"
    :height="size"
    viewBox="0 0 48 48"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    :style="svgStyle"
    :class="svgClass"
  >
    <g id="AddOutline-AddOutline" stroke="none" :stroke-width="1" fill="none" fill-rule="evenodd">
      <g id="AddOutline-add">
        <rect
          id="AddOutline-矩形"
          fill="#FFFFFF"
          :opacity="0"
          :x="0"
          :y="0"
          :width="48"
          :height="48"
        />
        <path
          d="M25.1,6.5 C25.3209139,6.5 25.5,6.6790861 25.5,6.9 L25.5,22.5 L41.1,22.5 C41.3209139,22.5 41.5,22.6790861 41.5,22.9 L41.5,25.1 C41.5,25.3209139 41.3209139,25.5 41.1,25.5 L25.5,25.5 L25.5,41.1 C25.5,41.3209139 25.3209139,41.5 25.1,41.5 L22.9,41.5 C22.6790861,41.5 22.5,41.3209139 22.5,41.1 L22.5,25.5 L6.9,25.5 C6.6790861,25.5 6.5,25.3209139 6.5,25.1 L6.5,22.9 C6.5,22.6790861 6.6790861,22.5 6.9,22.5 L22.5,22.5 L22.5,6.9 C22.5,6.6790861 22.6790861,6.5 22.9,6.5 L25.1,6.5 Z"
          id="AddOutline-路径"
          fill="currentColor"
          fill-rule="nonzero"
        />
      </g>
    </g>
  </svg>
</template>

<script setup lang="ts">
import { computed, useAttrs, type CSSProperties } from 'vue'

interface Props {
  size?: string | number
  color?: string
  className?: string
}

const props = withDefaults(defineProps<Props>(), {
  size: '1em',
  color: undefined,
  className: '',
})

const attrs = useAttrs()

const svgStyle = computed<CSSProperties>(() => {
  const baseStyle: CSSProperties = {
    verticalAlign: '-0.125em',
    width: props.size,
    height: props.size,
  }

  if (props.color) {
    baseStyle.color = props.color
  }

  const attrsStyle = attrs.style as CSSProperties | undefined

  return {
    ...baseStyle,
    ...attrsStyle,
  }
})

const svgClass = computed<string>(() => {
  const classes = ['antd-mobile-icon']

  if (props.className) {
    classes.push(props.className)
  }

  if (attrs.class) {
    if (Array.isArray(attrs.class)) {
      classes.push(...attrs.class.filter(Boolean))
    } else if (typeof attrs.class === 'string') {
      classes.push(attrs.class)
    }
  }

  return classes.filter(Boolean).join(' ')
})

defineOptions({
  name: 'AddOutline',
  inheritAttrs: false,
})
</script>

<style scoped>
.antd-mobile-icon {
  display: inline-block;
}
</style>
