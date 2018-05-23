<template>
  <div class="publications-table">
    <div class="row controls-row">
      <div class="col-md-6">
        <b-form-input v-model="searchString"
                      size="sm"
                      type="text"
                      placeholder="Search" />
      </div>
      <div class="col-md-6 select-fields">
        <b-form-select v-model="selectedState" size="sm" :options="states"/>
        <b-form-select v-model="selectedGrade" size="sm" :options="grades"/>
        <b-form-select v-model="selectedStatus" size="sm" :options="statuses"/>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12 pt-3">
        <b-table striped hover :items="items" :fields="fields"></b-table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PublicationsTable',
  data () {
    return {
      searchString: '',
      selectedState: null,
      selectedGrade: null,
      selectedStatus: null,
      states: [
        { value: 'Al', text: 'Alabama' }
      ],
      grades: [
        { value: '1', text: 'A' }
      ],
      statuses: [
        { value: 'outlined', text: 'Outlined' }
      ],
      fields: [
        {
          key: 'publication_title'
        },
        {
          key: 'state_&_grade',
          label: 'State & Grade'
        },
        {
          key: 'sku'
        },
        {
          key: 'year'
        },
        {
          key: 'status'
        },
        {
          key: 'actions'
        }
      ],
      items: [{
        publication_title: '3',
        'state_&_grade': 'fd',
        sku: 'f',
        year: '444',
        status: 'v',
        actions: 'vv'
      }]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .publications-table {
    padding: 0 15px;
  }
  .select-fields select {
    width: 30%;
  }
</style>
