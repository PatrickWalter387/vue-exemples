<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld v-if="visivel" v-bind:msg="nome"/>
  <p v-else>OLA MUNDO</p>

  <input type="text" v-model="comentario" v-on:change="() => console.log(comentario)" />
  <button v-on:click="() => postarComentario()">Click</button>

  <CompComentario :msg="mensagem" v-for="(mensagem, index) in comentarios" :key="index" />

  <h3>Total de mensagens: {{totalComentarios()}} mensagens</h3>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import CompComentario from './components/CompComentario.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    CompComentario
  },
  
  data() {
    return {
      nome: "Patrick",
      visivel: true,
      comentario: "",
      comentarios: []
    }
  },

  methods: {
    postarComentario() {
      this.comentarios.push(this.comentario);
      this.comentario = "";
    },

    totalComentarios() {
      return this.comentarios.length;
    }
  }
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
