<template>
  <button class="h-button" :disabled="props.disabled" :class="styleClass" @click="handleClick">
    <slot />
  </button>
</template>
<script setup lang="ts">
import { computed, toRefs } from 'vue'
import { ButtonProps } from './button'
const props = defineProps(ButtonProps)
const emits = defineEmits(['click'])

const handleClick = () => {
  emits('click')
}

const { icon } = toRefs(props)
const styleClass = computed(() => {
  return {
    [`h-button--${props.type}`]: props.type,
    [`h-button--${props.size}`]: props.size,
    'is-plain': props.plain,
    'is-round': props.round,
    'is-disabled': props.disabled
  }
})
</script>

<script lang="ts">
import '../../../../theme-chalk/src/button.less'
export default {
  name: 'HButton'
}
</script>
