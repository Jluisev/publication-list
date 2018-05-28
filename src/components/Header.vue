<template>
  <b-navbar type="dark" variant="dark">
    <b-navbar-brand href="#">
      Back<span class="logo-s">s</span><span class="logo-t">t</span><span class="logo-a">a</span>ge
    </b-navbar-brand>
    <b-navbar-nav>
      <b-nav-item-dropdown size="sm" text="Editorial">
        <b-dropdown-item>
          Browse
        </b-dropdown-item>
        <b-dropdown-item>
          Config
        </b-dropdown-item>
      </b-nav-item-dropdown>
    </b-navbar-nav>
    <b-navbar-nav class="ml-auto right-side">
      <b-nav-item-dropdown size="sm" text="Melissa">
        <b-dropdown-item>
          Profile
        </b-dropdown-item>
        <b-dropdown-item>
          Sign out
        </b-dropdown-item>
      </b-nav-item-dropdown>
    </b-navbar-nav>
  </b-navbar>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style>
  .dropdown-menu.show {
    position: absolute;
  }
  .right-side .dropdown-menu.show {
    left: -120%;
  }
  .logo-s {
    color: #dd8e8d;
  }
  .logo-t {
    color: #eaca62;
  }
  .logo-a {
    color: #8bbf79;
  }
</style>
