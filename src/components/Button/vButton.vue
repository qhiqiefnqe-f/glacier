<template>
  <button
    ref="_ref"
    class="vk-button"
    :class="{
      'is-plain': plain,
      'is-round': round,
      'is-circle': circle,
      'is-disabled': disabled,
      [`vk-button--${type}`]: type,
      [`vk-button--${size}`]: size
    }"
    :disabled="disabled"
    :autofocus="autofocus"
    :type="nativeType"
  >
    <!-- 上面这三个是原生的属性 -->
    <span>
      <slot></slot>
    </span>
  </button>
  <!-- 这里的动态disabled类是button自带的 -->
</template>

<script setup lang="ts">
import type { ButtonProps } from './types'
import { ref } from 'vue'
withDefaults(defineProps<ButtonProps>(), {
  nativeType: 'button'
})

defineOptions({
  name: 'VButton'
})

const _ref = ref<HTMLButtonElement>()

defineExpose({
  ref: _ref
})
</script>

<style scoped lang="scss">
.vk-button {
  height: 32px;
  width: 100px;
}
</style>
