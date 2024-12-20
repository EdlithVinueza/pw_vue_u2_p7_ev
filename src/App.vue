<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <Contador encabezado="Contador Primero j" v-bind:valor="calcular(1, 3)" :esVerdad="muestra1" :valor2="78"/>
  <Contador encabezado="Contador Segundo" v-bind:valor="calcular(5, 3)" v-bind:esVerdad="muestra2" />
  <button @:click="cambiar(1)">Cambiar Primero</button>
  <button @:click="cambiar(2)">Cambiar Segundo</button>
</template>


<script>
import Contador from './components/Contador.vue';

export default {
  name: 'App',
  components: {
    Contador
  },
  data() {
    return {
      muestra1:true,
      muestra2:true
    };
  },
  methods: {
    calcular(a, b) {
      return a + b;
    },
    calcular2(a, b) {
      return "HolaMundo";
    },
    calcular3() {
      return ;
    },
    cambiar(valor) {
      if (valor === 1) {
        this.muestra1 = !this.muestra1;
      }
      if (valor === 2){
      this.muestra2 = !this.muestra2;
      }
    }
  },

}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>