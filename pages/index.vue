<template>
  <div class="page">
    <Navbar></Navbar>
    <h1>Aprendendo vue 2/ Nuxt</h1>
  </div>
</template>

<script>
import Calculator from "~/components/Calculator.vue";
import Navbar from "~/components/Navbar.vue";
export default {
  name: "IndexPage",
  components: { Calculator, Navbar },
};
</script>

<style>
h1{
  font-size: 2rem;
}
</style>
