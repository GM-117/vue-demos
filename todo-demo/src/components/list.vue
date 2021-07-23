<template>
  <div class="list">
    <input
      type="text"
      class="add-input"
      autofocus="autofocus"
      placeholder="What need to be done"
      @keyup.enter="addTodo"
    />
    <Items
      v-for="todo in filterTodos"
      :todo="todo"
      :key="todo.id"
      @del="deleteTodo"
    />
    <Footer
      :filter="filter"
      :todos="todos"
      @toggle="toggleFilter"
      @clearAll="clearAllCompletedTodo"
    />  
  </div>
</template>

<script>
import Items from "./list-items.vue";
import Footer from "./footer.vue";

let id = 0;
export default {
  data() {
    return {
      todos: [],
      filter: "all",
    };
  },
  components: {
    Items,
    Footer,
  },
  computed: {
    filterTodos() {
      if (this.filter == "all") {
        return this.todos;
      }
      const filterCompleted = this.filter == "completed";
      return this.todos.filter((todo) => todo.completed == filterCompleted);
    },
  },
  methods: {
    addTodo(e) {
      console.log(e);
      this.todos.unshift({
        id: id++,
        content: e.target.value,
        completed: false,
      });
      // console.log(this.todos)
      console.log(`id ${id}`)
      e.target.value = "";
    },
    deleteTodo(id) {
      this.todos.splice(
        this.todos.findIndex((todo) => id == todo.id),
        1
      );
    },
    toggleFilter(state) {
      console.log(state);
      this.filter = state;
    },
    clearAllCompletedTodo() {
      this.todos = this.todos.filter((todo) => todo.completed == false);
    },
  },
};
</script>

<style scoped>
  .list{
    width: 600px;
    margin: 0 auto;
    box-shadow: 0 0 5px #666;
  }
  .add-input{
    position: relative;
    width: 100%;
    font-size: 24px;
    line-height: 24px;
    border: none;
    outline: none;
    box-shadow: 0 -2px 1px rgba(0, 0, 0, 0.03);
    box-sizing: border-box;
    padding: 16px 16px 16px 36px;
  }
</style>