<template>
  <List :items="users" :fields="['username', 'name']">
    <template #header="{ item: user }">
      {{ user.name }} ({{ user.username }})
    </template>
  </List>
  <List :items="todos" :fields="['title']">
    <template #header="slotScoped">
      <Todo :footer="slotScoped.item" />
    </template>
  </List>
</template>

<script>
import { loadUsers, loadTodo } from "./api";
import List from "./components/List.vue";
import Todo from "./components/Todo.vue";
export default {
  name: "App",
  data() {
    return {
      users: [],
      todos: [],
    };
  },
  components: { List, Todo },
  mounted() {
    loadUsers().then((users) => (this.users = users));
    loadTodo().then((todos) => (this.todos = todos));
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
