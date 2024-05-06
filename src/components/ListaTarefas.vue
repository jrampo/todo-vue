<script setup>
    
</script>

<template>
  <ul class="list-group mt-4">
    <li class="list-group-item" v-for="tarefa in tarefasFiltradas">
      <input v-model="tarefa.finalizada" :id="tarefa.titulo" type="checkbox" />
      <label
        class="ms-3"
        :for="tarefa.titulo"
        :class="{ done: tarefa.finalizada }"
      >
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>
</template>
