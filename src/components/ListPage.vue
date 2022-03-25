<template>
  <div class="list">
    <ul>
      <li v-for="(item, i) in tarea" :key="i">
        {{ i }} - {{ item.item }}
        <button @click="borrar(i)" class="btn btn-light">Eliminar</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ListPage",
  props: {
    tarea: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    borrar(i) {
      this.$emit("borrarPadre", i);
    },
  },
};
</script>
