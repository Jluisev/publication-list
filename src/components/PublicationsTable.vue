<template>
  <div class="publications-table">
    <div class="row controls-row">
      <div class="col-md-12 filters-row">
        <b-form-input v-model="searchString"
                      class="search-input"
                      size="sm"
                      type="text"
                      placeholder="Search" />
        <b-form-select v-model="selectedState" size="sm" :options="states">
          <option :value="null">All States</option>
        </b-form-select>
        <b-form-select v-model="selectedGrade" size="sm" :options="grades">
          <option :value="null">All Grades</option>
        </b-form-select>
        <b-form-select v-model="selectedStatus" size="sm" :options="statuses">
          <option :value="null">All Statuses</option>
        </b-form-select>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12 pt-3">
        <b-table :filter="searchString" show-empty hover head-variant="light" :items="items" :fields="fields">
          <template slot="publication_title" slot-scope="data">
            <a :href="'#'" v-b-modal.modal-1 v-on:click="$emit('open-modal')">
              {{data.value}}
            </a>
          </template>
          <template slot="actions" slot-scope="data">
            <b-dropdown id="actions" variant="outline-secondary" text="Actions" size="sm">
              <b-dropdown-item-button v-b-modal.modal-1>Edit</b-dropdown-item-button>
              <b-dropdown-item-button @click="deletePost">Delete</b-dropdown-item-button>
            </b-dropdown>
          </template>
        </b-table>
      </div>
    </div>
  </div>
</template>

<script>
import { states, grades, statuses, publications } from '../constants'
export default {
  name: 'PublicationsTable',
  data () {
    return {
      searchString: '',
      selectedState: null,
      selectedGrade: null,
      selectedStatus: null,
      states,
      grades,
      statuses,
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
      items: publications
    }
  },
  methods: {
    deletePost () {
      this.$swal({
        text: 'Would you like to delete this publication?',
        type: 'warning',
        showCancelButton: true,
        cancelButtonColor: '#3085d6',
        confirmButtonColor: '#d33',
        confirmButtonText: 'Delete Publication',
        cancelButtonText: 'Keep Publication'
      }).then((result) => {
        if (result.value) {
          this.$swal(
            'Deleted!',
            'The publication has been deleted.',
            'success'
          )
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .publications-table {
    padding: 0 15px;
  }
  .filters-row {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
  .filters-row .search-input {
    width: 50%;
  }
  .filters-row select {
    width: 15%;
  }
</style>
