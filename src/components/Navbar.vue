<template>
  <div>
    <b-navbar class="navbarStyle" toggleable>
      <b-navbar-brand>Navbar</b-navbar-brand>
      <b-navbar-toggle class="colorBtn" target="navbar-toggle-collapse">
        <template #default="{ expanded }">
          <b-icon v-if="expanded" icon="chevron-bar-up"></b-icon>
          <b-icon v-else icon="cevron-bar-down"></b-icon>
        </template>
      </b-navbar-toggle>
      <b-collapse id="navbar-toggle-collapse" is-nav>
        <div class="d-flex justify-content-end">
          <b-navbar-nav class="ml-auto">
            <b-nav-item href="#"
              ><router-link to="/">Home</router-link></b-nav-item
            >
            <b-nav-item href="#"
              ><router-link to="/Login">Login</router-link></b-nav-item
            >
          </b-navbar-nav>
        </div>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {}
</script>

<style>
#nav {
background: rgba( 233, 196, 106, 0.9 );
box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
backdrop-filter: blur( 0.5px );
-webkit-backdrop-filter: blur( 0.5px );

border: 1px solid rgba( 255, 255, 255, 0.18 );
  margin-bottom: 3rem;
}
.colorBtn {
    background: rgba(231, 111, 81, 0.719);
box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
backdrop-filter: blur( 20px );
-webkit-backdrop-filter: blur( 20px );
border-radius: 10px;
border: 1px solid rgba( 255, 255, 255, 0.18 );
}
</style>
