<template>
  <div>
      <ul v-for="todo in $data.todos.filter(shouldShowTodo)" :key="todo.key">
          <li v-bind:class="{complete: todo.done}">
              {{ todo. text }}
              <input type="checkbox" v-model="todo.done">
          </li>
      </ul>
      <form v-on:submit="handleAddTodo($event)">
          <input type="text" v-model="input">
      </form>
      <label  class="show-completed">
          Show Completed Items?
          <input type="checkbox" v-model="showDone">
      </label>
  </div>
</template>

<script>
    export default {
        methods: {
            handleAddTodo(e) {
                e.preventDefault();
                this.$data.todos.push({text:this.input, done:false});
                this.input = "";
            },
            shouldShowTodo(todo) {
                if (this.$data.showDone) {
                    return true;
                } else {
                    return !todo.done;
                }
            }
        },
        data() {
            return this.$props.state;
        },
        props:['state']
    }
</script>
<style>
    body {
        font-family: Helvetica, sans-serif;
        color: darkslategray;
        font-size: 1.2em;
        margin: 1.4em;
        position: relative;
    }
    input[type=text] {
        margin-top: 1em;
        height:30px;
        width: 100%;
        font-size: 1.7em;
        margin-bottom: 2em;

    }
    input[type=checkbox] {
        position: absolute;
        right: 0;
        padding: 1em;
        cursor: pointer;
    }
    li {
        list-style-type: none;
        padding: 1em 0 1em 0;
        position: relative;
    }
    li input {
        transform: scale(1.8);
    }
    ul {
        padding: 0;
    }
    label {
        width: 80%
    }
    .complete {
        color: gainboro;
        text-decoration: line-through;
        font-style: italic;
    }

    .show-completed {
        font-size: 1em;
        color: slategray;
    }
    .show-completed input {
        transform: scale(1.4);
    }
</style>


