<template>
  <div class="publication-list">
    <Header />
    <div class="col-md-12">
      <b-button size="sm" variant="primary" class="float-right" v-b-modal.modal-1>Create Publication</b-button>
    </div>
    <PublicationsTable />
    <b-modal hide-footer id="modal-1" size="lg" title="Create Publication">
      <PublicationForm />
    </b-modal>
  </div>
</template>

<script>
import Header from './Header.vue'
import PublicationsTable from './PublicationsTable.vue'
import PublicationForm from './PublicationForm.vue'
export default {
  components: {
    Header,
    PublicationsTable,
    PublicationForm
  },
  name: 'PublicationList'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .col-md-12 {
    padding: 15px;
    height: 65px;
  }
</style>
