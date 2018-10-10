<template>
    <section class="todo-section">
        <div class="todo-heading">
            <h2>ToDo list</h2>
            <div class="todo-add">
                <input v-model="todoText" :class='{error: hasError}' type="text" class="todo-input" placeholder="Type your todo">
                <a href="#" @click.prevent="addTodo" class="btn">Add</a>
            </div>
        </div>
        <ul v-show="todoItems" class="todo-list">
            <li v-for="(todo, index) in todoItems"> 
                <span>
                    {{index}} {{todo}} 
                </span>
                <a href="#" @click.prevent="removeTodo" class="btn-close"></a>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
  data() {
    return {
      hasError: false,
      todoText: "",
      todoItems: []
    };
  },
  methods: {
    addTodo: function() {
      if (this.todoText) {
        this.hasError = false;
        this.todoItems.push(this.todoText);
        this.todoText = "";
      } else {
        this.hasError = true;
      }
    },
    removeTodo: function() {}
  }
};
</script>

<style>
.todo-section {
  margin: 30px;
  padding: 10px 15px;
  border: 1px solid var(--main-border-green);
  border-radius: var(--radius);
  background-color: var(--main-green);
  box-shadow: var(--main-shadow);
}
.todo-heading {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
}
.todo-heading h2 {
  margin-right: 20px;
}
.todo-add {
  display: flex;
  flex-grow: 1;
  justify-content: flex-end;
}
.todo-add input {
  width: 100%;
  max-width: 237px;
  margin-right: 10px;
}
.todo-list {
  padding: 15px 20px;
  border: 1px solid var(--main-border-green);
  border-radius: var(--radius);
  background-color: var(--main-white);
  box-shadow: var(--main-shadow);
  list-style: none;
}
.todo-list {
  position: relative;
}
</style>

