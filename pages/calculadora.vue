<template>
  <div class="page">
    <Navbar></Navbar>
    <!-- <router-link to="/teste">teste</router-link> -->
    <Calculator />
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
.page,
html,
body,
#__nuxt,
#__layout {
  height: 100%;
  width: 100%;
}

.page {
  display: flex;
  flex-direction: column;
}
</style>
