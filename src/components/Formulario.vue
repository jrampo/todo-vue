<script setup>
const props = defineProps(["adicionarTarefa", "novaTarefa", "filtro"]);
</script>

<template>
  <form @submit.prevent="props.adicionarTarefa">
    <div class="row d-flex justify-content-between">
      <div class="col">
        <input
          v-model="props.novaTarefa"
          type="text"
          placeholder="Digite aqui a descrição da tarefa"
          class="form-control"
        />
      </div>
      <div class="col-md-2">
        <button type="submit" class="btn btn-primary ms-4">Cadastrar</button>
      </div>
      <div class="col-md-2">
        <select v-model="props.filtro" class="form-control">
          <option value="todas">Todas as tarefas</option>
          <option value="pendentes">Tarefas pendentes</option>
          <option value="finalizadas">Tarefas finalizadas</option>
        </select>
      </div>
    </div>
  </form>
</template>
