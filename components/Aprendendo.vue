<template>
  <div>
    <div class="card">
      <span>Olá mundo</span>
      <span>{{ banana }}</span>
      <input type="text" @keydown.enter="teste" v-model="texto" />
      <button v-on:click="teste" >enviar</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      banana: "oioi",
      texto: "",
      array: ""
    };
  },
  methods: {
    teste: function () {
      this.banana = this.texto;
      this.texto = ""
    },
    sum: function(){
        let conta = this.texto
        console.log({conta})
        conta = eval(conta)
        console.log({conta})
    }
  },
};
</script>

<style scoped>
div {
  display: flex;
  justify-content: center;
}
.card {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  text-align: center;
  align-items: center;
  width: 300px;
  padding: 1rem;
  background-color: antiquewhite;
}
input {
  border: 1px solid black;
}
button{
    margin-top: 0.5rem;
    width: 50%;
    background-color: green;
}
</style>
