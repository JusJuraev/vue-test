<template>
  <row class="row" :spacing="50">
    <column :span="2">
      <button class="toggle-button" v-if="item.children" type="button" @click="toggle">
        {{ isOpen ? '-' : '+' }}
      </button>
    </column>
    <column :span="12">
      <div :style="`padding-left: ${level * 20}px`">{{ item.name }}</div>
    </column>
    <column :span="10">
      {{ item.test }}
    </column>
  </row>

  <div v-if="isOpen">
    <table-row
      :key="child.id"
      v-for="child in item.children"
      :item="child"
      :level="getLevel + 1"
    />
  </div>
</template>

<script>
  import Row from '@/components/Row'
  import Column from '@/components/Column'

  export default {
    name: 'TableRow',
    components: {
      Row,
      Column
    },
    props: {
      level: {
        default: 0,
        type: Number
      },
      item: {
        id: Number,
        name: String,
        test: String,
        children: Array
      }
    },
    data: () => {
      return {
        isOpen: false
      }
    },
    methods: {
      toggle () {
        this.isOpen = !this.isOpen
      }
    },
    computed: {
      getLevel () {
        return this.level || 0
      }
    }
  }
</script>

<style scoped lang="scss">
  .row {
    padding: 5px 15px;
    margin-bottom: 10px;
    &:nth-child(odd) {
      background: #fafafa;
    }
  }
  .toggle-button {
    border: none;
    background: #efefef;
    cursor: pointer;
    width: 30px;
    text-align: center;
    &:hover {
      background: #cecece;
    }
  }
</style>