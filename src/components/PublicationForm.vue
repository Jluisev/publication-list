<template>
  <div class="publication-form">
    <b-form>
      <div class="row">
        <div class="col">
          <b-form-group id="title"
                        label="Title"
                        label-for="title-input">
            <b-form-input id="title-input"
                          type="text"
                          v-model="form.title"
                          required
                          placeholder="Title">
            </b-form-input>
          </b-form-group>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <b-form-group id="subject"
                        label="Subject"
                        label-for="subject-input">
            <b-form-select id="subject-input"
                           :options="subjects"
                           v-model="form.subject"
                           required>
              <option :value="null">Subject</option>
            </b-form-select>
          </b-form-group>
        </div>
        <div class="col">
          <b-form-group id="school-year"
                        label="School Year"
                        label-for="school-year-input">
            <b-form-select id="school-year-input"
                           v-model="form.schoolYear"
                           :options="schoolYears"
                           required
                           placeholder="School Year">
              <option :value="null">School Year</option>
            </b-form-select>
          </b-form-group>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <b-form-group id="state"
                        label="State"
                        label-for="state-input">
            <b-form-select id="state-input"
                           :options="states"
                           v-model="form.state"
                           required>
              <option :value="null">State</option>
            </b-form-select>
          </b-form-group>
        </div>
        <div class="col">
          <b-form-group id="grade"
                        label="Grade"
                        label-for="grade-input">
            <b-form-select id="grade-input"
                           v-model="form.grade"
                           :options="grades"
                           required
                           placeholder="Grade">
              <option :value="null">Grade</option>
            </b-form-select>
          </b-form-group>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <b-form-group id="language"
                        label="Language"
                        label-for="language-input">
            <b-form-select id="language-input"
                           :options="languages"
                           v-model="form.language"
                           required
                           placeholder="Language">
              <option :value="null">Language</option>
            </b-form-select>
          </b-form-group>
        </div>
        <div class="col">
          <b-form-group id="format"
                        label="Format"
                        label-for="format-input">
            <b-form-select id="format-input"
                           v-model="form.format"
                           :options="formats"
                           required
                           placeholder="Format">
              <option :value="null">Format</option>
            </b-form-select>
          </b-form-group>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <b-form-group id="issn"
                        label="ISSN"
                        label-for="issn-input">
            <b-form-input id="issn-input"
                          type="input"
                          v-model="form.issn"
                          placeholder="ISSN">
            </b-form-input>
          </b-form-group>
        </div>
        <div class="col">
          <b-form-group id="isbn"
                        label="ISBN"
                        label-for="isbn-input">
            <b-form-input id="isbn-input"
                          type="text"
                          v-model="form.isbn"
                          required
                          placeholder="ISBN">
            </b-form-input>
          </b-form-group>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <b-form-group id="sku"
                        label="SKU"
                        label-for="sku-input">
            <b-form-input id="sku-input"
                          type="text"
                          v-model="form.sku"
                          required
                          placeholder="SKU">
            </b-form-input>
          </b-form-group>
        </div>
      </div>
      <div class="modal-footer">
        <b-button @click="hideModal" class="float-right" variant="default">
          Cancel
        </b-button>
        <b-button @click="handleSubmit" class="float-right" variant="primary">
          Create Publication
        </b-button>
      </div>
    </b-form>
  </div>
</template>
<script>
import {languages, states, grades, schoolYears, formats, subjects} from '../constants'

export default {
  props: ['selectedPublication'],
  data () {
    return {
      form: this.selectedPublication || {
        title: '',
        subject: null,
        schoolYear: null,
        state: null,
        grade: null,
        language: null,
        format: null,
        issn: '',
        isbn: '',
        sku: ''
      },
      languages,
      states,
      grades,
      schoolYears,
      formats,
      subjects
    }
  },
  methods: {
    onSubmit (evt) {
      if (evt) evt.preventDefault()
      this.$swal({
        text: 'You successfully added a new publication. Would you like to edit the Scope and Sequence at this time?',
        type: 'success',
        showCancelButton: true,
        cancelButtonText: 'Go back to Publications',
        confirmButtonText: 'Edit Scope and Sequence',
        reverseButtons: true
      }).then((result) => {
        if (result.value) {
          window.open('http://www.studiesweekly.com', '_blank')
        }
      })
    },
    onReset (evt) {
      if (evt) evt.preventDefault()
      this.form = {
        title: '',
        subject: null,
        schoolYear: null,
        state: null,
        grade: null,
        language: null,
        format: null,
        issn: '',
        isbn: '',
        sku: ''
      }
    },
    handleSubmit () {
      this.onSubmit()
      this.$root.$emit('bv::hide::modal', 'modal-1')
    },
    hideModal () {
      this.$root.$emit('bv::hide::modal', 'modal-1')
    }
  }
}
</script>
<style>

</style>
