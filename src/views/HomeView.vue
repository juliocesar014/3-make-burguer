<template>
  <BannerComponente />
  <div class="main-container">
    <h1>Monte o seu Burguer:</h1>
    <FormComponente />
  </div>
</template>

<script>
import BannerComponente from "@/components/BannerComponente.vue";
import FormComponente from "@/components/FormComponente.vue";

export default {
  name: "HomeView",
  components: {
    BannerComponente,
    FormComponente,
  },
};
</script>

<style scoped>
h1 {
  color: #222;
}
</style>
