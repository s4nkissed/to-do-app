<template>
  <button class="button" :style="{backgroundColor: color}">
    <slot>

    </slot>
  </button>
</template>

<script setup>

defineProps({
  color: {
    type: String,
    default: '#e69690'
  }
})

</script>

<style lang="scss" scoped>
.button {
  border: none;
  padding: 6px;
  border-radius: 5px;
  font-weight: 600;
  box-shadow: 0 0 2px black;
}
</style>