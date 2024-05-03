<script setup>
const estado = reactive({
  tarefas: [
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
  ],
});
</script>

<template>
  <div class="container">
    <header class="p-5 my-4 bg-light rounded-3">
      <h1>Minhas tarefas</h1>
      <p>Você possui 7 tarefas pendenter</p>
    </header>
    <form>
      <div class="row d-flex justify-content-between">
        <div class="col">
          <input
            type="text"
            placeholder="Digite aqui a descrição da tarefa"
            class="form-control"
          />
        </div>
        <div class="col-md-2">
          <button type="submit" class="btn btn-primary ms-4">Cadastrar</button>
        </div>
        <div class="col-md-2">
          <select class="form-control">
            <option value="todas">Todas as tarefas</option>
            <option value="pendentes">Tarefas pendentes</option>
            <option value="finalizadas">Tarefas finalizadas</option>
          </select>
        </div>
      </div>
    </form>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="tarefa in estado.tarefas">
        <input
          :checked="tarefa.finalizada"
          :id="tarefa.titulo"
          type="checkbox"
        />
        <label
          class="ms-3"
          :for="tarefa.titulo"
          :class="{ done: tarefa.finalizada }"
        >
          {{ tarefa.titulo }}
        </label>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
