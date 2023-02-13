<template>
  <NavbarComponente :logo="logo_src" :alt="app_name" />
  <router-view />
  <FooterComponente />
</template>

<style></style>

<script>
import NavbarComponente from "./components/NavbarComponente.vue";
import FooterComponente from "./components/FooterComponente.vue";

export default {
  components: { NavbarComponente, FooterComponente },
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make Your Burguer",
    };
  },
};
</script>

<style>
* {
  font-family: Arial, Helvetica, sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #2222;
}
</style>
