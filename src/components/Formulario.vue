<script setup>
const props = defineProps([
  "cadastraTarefa",
  "tarefaTemp",
  "trocarFiltro",
  "editaTarefaTemp",
]);
</script>

<template>
  <form @submit.prevent="props.cadastraTarefa">
    <div class="row">
      <div class="col">
        <input
          :value="props.tarefaTemp"
          @change="props.editaTarefaTemp"
          required
          type="text"
          placeholder="Digite aqui a descrição da tarefa"
          class="form-control"
        />
      </div>
      <div class="col-md-2 d-flex justify-content-center align-items-center">
        <button type="submit" class="btn btn-success my-3 my-lg-0">
          Cadastrar tarefa
        </button>
      </div>
      <div class="col-md-2">
        <select @change="props.trocarFiltro" class="form-control">
          <option value="todas">Todas tarefas</option>
          <option value="pendentes">Tarefas pendentes</option>
          <option value="finalizadas">Tarefas finalizadas</option>
        </select>
      </div>
    </div>
  </form>
</template>
