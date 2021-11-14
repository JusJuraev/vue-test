<template>
  <div class="row" :style="`column-gap: ${spacing}px`">
    <slot />
  </div>
</template>

<script>
  export default {
    name: 'Row',
    props: {
      spacing: Number
    }
  }
</script>

<style scoped lang="scss">
  .row {
    display: flex;
  }
</style>