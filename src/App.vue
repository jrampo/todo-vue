<script setup>
import { ref, computed } from "vue";
import Cabecalho from "./components/Cabecalho.vue";
import Formulario from "./components/Formulario.vue";
import ListaTarefas from "./components/ListaTarefas.vue";

const tarefas = ref([
  {
    titulo: "Lavar louça",
    finalizada: false,
  },
  {
    titulo: "Tirar lixo",
    finalizada: false,
  },
  {
    titulo: "Estudar Vue.JS",
    finalizada: true,
  },
]);

const novaTarefa = ref("");
const filtro = ref("todas");

const adicionarTarefa = () => {
  if (novaTarefa.value.trim() !== "") {
    tarefas.value.push({ titulo: novaTarefa.value, finalizada: false });
    novaTarefa.value = "";
  }
};

const tarefasFiltradas = computed(() => {
  if (filtro.value === "pendentes") {
    return tarefas.value.filter((tarefa) => !tarefa.finalizada);
  } else if (filtro.value === "finalizadas") {
    return tarefas.value.filter((tarefa) => tarefa.finalizada);
  } else {
    return tarefas.value;
  }
});

const tarefasPendentes = computed(() => {
  return tarefas.value.filter((tarefa) => !tarefa.finalizada).length;
});
</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes="tarefasPendentes().length" />
    <Formulario :nova-tarefa="estado.novaTarefa" />
    <ListaTarefas />
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
