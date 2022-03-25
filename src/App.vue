<template>
  <div id="app">
    <h1 class="my-5">{{ titulo }}</h1>
    <span>{{ texto }}</span>
    <input
      type="text"
      placeholder="Ingresa nueva tarea"
      v-model="nuevaTarea"
      class="mx-2"
    />
    <button v-on:click="crearTarea" id="btn">Crear</button>
    <h2 class="my-5">{{ subtitulo }}</h2>
    <ListPage :tarea="tareas" @borrarPadre="borrarPadre" />
  </div>
</template>

<script>
import ListPage from "./components/ListPage.vue";
export default {
  name: "App",
  components: {
    ListPage,
  },
  data() {
    return {
      titulo: "Crea una nueva tarea",
      subtitulo: "Lista",
      texto: "Tarea",
      tareas: [
        {
          item: "Ir al supermercado",
        },
        {
          item: "Pagar Internet",
        },
        {
          item: "Pagar Netflix",
        },
      ],
      nuevaTarea: "",
    };
  },
  methods: {
    crearTarea() {
      this.tareas.push({
        item: this.nuevaTarea,
      });
      this.nuevaTarea = "";
    },
    borrarPadre(i) {
      this.tareas.splice(i, 1);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.list {
  text-align: left;
  width: 300px;
  margin: auto;
}

.btn {
  border: 1px solid gray;
  margin: 5px;
  width: 90px;
  height: 35px;
}
#btn {
  border-radius: 10%;
  border: 5px solid blue;
}
</style>
