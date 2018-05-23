<template>
  <div class="publication-list">
    <Header />
    <div class="col-md-12">
      <button class="btn btn-sm btn-primary float-right">Create Publication</button>
    </div>
    <PublicationsTable />
  </div>
</template>

<script>
import Header from './Header.vue'
import PublicationsTable from './PublicationsTable.vue'
export default {
  components: {
    Header,
    PublicationsTable
  },
  name: 'PublicationList',
  data () {
    return {
      msg: 'Publication List'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .col-md-12 {
    padding: 15px;
    height: 65px;
  }
</style>
