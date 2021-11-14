<template>
  <div class="col" :style="`flex-basis: ${getFlexBasis}`">
    <slot />
  </div>
</template>

<script>
  export default {
    name: 'Col',
    props: {
      span: Number
    },
    computed: {
      getFlexBasis () {
        const maxColumnsCount = 24
        const flexBasisValue = (this.props.span / maxColumnsCount) * 100
        return this.props.span ? `${flexBasisValue}%` : 'unset'
      }
    }
  }
</script>

<style scoped lang="scss">
  .col {
    flex-grow: 1;
  }
</style>