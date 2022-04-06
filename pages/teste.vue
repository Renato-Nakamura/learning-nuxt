<template>
  <div>
    <Navbar></Navbar>
    <Aprendendo></Aprendendo>
  </div>
</template>

<script>
import Aprendendo from "../components/Aprendendo.vue";
import Navbar from "~/components/Navbar.vue";
export default {
  name: "testeRoute",
  components: { Aprendendo, Navbar },
};
</script>
