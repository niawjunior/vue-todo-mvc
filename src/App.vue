<template>
  <div>
      <ul v-for="todo in $data.todos" :key="todo.key">
          <li>
              {{ todo. text }}
          </li>
      </ul>
      <form v-on:submit="handleAddTodo($event)">
          <input type="text" v-model="input">
      </form>
  </div>
</template>

<script>
    export default {
        methods: {
            handleAddTodo(e) {
                e.preventDefault();
                this.$data.todos.push({text:this.input, done:false});
                this.input = "";
            }
        },
        data() {
            return this.$props.state;
        },
        props:['state']
    }
</script>

<style>

</style>


