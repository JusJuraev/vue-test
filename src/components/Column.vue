<template>
  <div class="col" :style="`flex-basis: ${getFlexBasis}`">
    <slot />
  </div>
</template>

<script>
  export default {
    name: 'Column',
    props: {
      span: Number
    },
    computed: {
      getFlexBasis () {
        const maxColumnsCount = 24
        const flexBasisValue = (this.span / maxColumnsCount) * 100
        return this.span ? `${flexBasisValue}%` : 'unset'
      }
    }
  }
</script>

<style scoped lang="scss">
  .col {
    flex-grow: 1;
  }
</style>