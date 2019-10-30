<template>
  <div>
    <button class="button is-warning" @click="getTodos()">Informacion</button>
    <table>
        <thead>
            <tr>
                <th>id</th>
                <th>completed</th>
                <th>title</th>
                <th>userid</th>
            </tr>
        </thead>
      <tbody>
        <tr v-for="todo in todos" :key="todo.id">
          <td>{{ todo.id }}</td>
          <td>{{ todo.completed }}</td>
          <td>{{ todo.title }}</td>
          <td>{{ todo.userId }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      todos: null
    };
  },
  /*  mounted() {
    this.getTodos();
  }, */
  methods: {
    async getTodos() {
      await axios
        .get("https://jsonplaceholder.typicode.com/todos")
        .then(response => {
          this.todos = response.data;
        });
      /* .catch(e => console.log(e)) */
    }
  }
};
</script>
<style  rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.7.5/css/bulma.css">
</style>