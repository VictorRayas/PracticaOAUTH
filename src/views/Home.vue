<template>
  <div class="home">
    <b-navbar v-if="$auth.isAuthenticated" style="background-color: beige;">
      <b-navbar-brand href="/profile">Perfil</b-navbar-brand>
    </b-navbar>
    <h1>Login con oauth</h1>
    <!-- Revisa la librería se encuentra cargando antes de mostrar los botones de acceso -->
    <div v-if="!$auth.loading">
      <!-- muestra el botón de login si no está autentificado -->
      <button style="background-color: blue; width: 10%; color: white;" v-if="!$auth.isAuthenticated" @click="login">Log in</button>
      <!-- muestra el botón de Log out si está autentificado -->
      <button style="background-color: red; width: 10%; color: white;" v-if="$auth.isAuthenticated" @click="logout">Log out</button>
    </div>

  </div>
</template>

<script>
export default {
  name: "home",

  methods: {
    login() {
      this.$auth.loginWithRedirect();
    },
    logout() {
      this.$auth.logout({
        logoutParams: {
          returnTo: window.location.origin,
        },
      });
    },
  },
};
</script>