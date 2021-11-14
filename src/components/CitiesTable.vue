<template>
  <div class="wrapper">
    <div class="search-box">
      <input
        class="search-box__input"
        type="text"
        @input="onSearch"
        placeholder="Search"
      />
    </div>

    <div class="table">
      <div class="table__overflow">
        <row class="row-header" :spacing="50">
          <column :span="2"></column>
          <column :span="12">Name</column>
          <column :span="10">Test</column>
        </row>
        <table-row :key="item.id" v-for="item in list" :item="item" />
      </div>
    </div>
  </div>
</template>

<script>
  import Row from '@/components/Row'
  import Column from '@/components/Column'
  import TableRow from '@/components/TableRow'
  import data from '../data.json'

  export default {
    name: 'HelloWorld',
    components: {
      Row,
      Column,
      TableRow
    },
    data () {
      return {
        list: data
      }
    },
    methods: {
      filterData (list = [], value = '') {
        const finder = ({ name }) => name.toLowerCase().includes(value)
        return list.reduce((result, item) => {
          const children = this.filterData(item.children, value)
          if (finder(item) || children.length) {
            children.length
              ? result.push({ ...item, children })
              : result.push(item)
          }

          return result
        }, [])
      },

      onSearch (event) {
        const searchValue = event.target.value.toLowerCase().trim()
        const filteredList = this.filterData(data, searchValue)
        this.list = searchValue ? filteredList : data
      }
    },
  }
</script>

<style scoped lang="scss">
  .wrapper {
    max-width: 1200px;
    margin: 0 auto;
    padding: 50px 25px;
  }
  .search-box {
    margin-bottom: 40px;
  }
  .search-box__input {
    border: 1px solid #777777;
    border-radius: 4px;
    padding: 2px 15px;
    width: 100%;
    height: 36px;
    outline: none;
  }

  .table {
    overflow-x: auto;
    & .table__overflow {
      min-width: 800px;
    }
  }
  .row-header {
    font-weight: bold;
    margin-bottom: 10px;
    padding: 5px 15px;
  }
</style>
