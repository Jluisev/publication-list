<template>
  <b-navbar type="dark" variant="dark" class="header">
    <b-navbar-brand href="#">{{ msg }}</b-navbar-brand>
    <b-navbar-nav>
      <b-nav-item-dropdown text="Editorial">
      </b-nav-item-dropdown>
    </b-navbar-nav>
    <b-navbar-nav class="ml-auto">
      <b-nav-item-dropdown text="Melissa">
      </b-nav-item-dropdown>
    </b-navbar-nav>
  </b-navbar>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      msg: 'Backstage'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .navbar-nav .dropdown-menu.show {
    position: absolute;
  }
</style>
