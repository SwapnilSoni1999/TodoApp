<template>
  <div class="container space-y-5 flex-col p-4">
    <!-- create card -->
    <div
      class="p-4 px-8 max-w-4xl w-full shadow-lg flex justify-between items-center space-x-3 rounded-lg"
    >
      <div class="w-full">
        <!-- <GradCheckbox @checked="check" :checkedStats="inputChecked">
        </GradCheckbox> -->
          <input
            type="text"
            class="outline-none w-full p-2"
            placeholder="Create new Todo"
            v-model="todoText"
            @keyup.enter="saveTodo"
          />
      </div>
      <div>
        <button @click="saveTodo" class="btn btn-gradient">Create</button>
      </div>
    </div>

    <div class="p-4 max-w-4xl w-full shadow-lg flex flex-col rounded-lg">
      <Todo
        v-for="(todo, index) in todos"
        :key="index"
        :todoText="todo.todoText"
        :checkedStats="todo.isChecked"
      />
      <span v-if="!todos.length" class="self-center text-gray-600"
        >No Todos noted.</span
      >
    </div>
  </div>
</template>

<script>
import Todo from "~/components/Todo";
import GradCheckbox from "~/components/Checkbox";

export default {
  data: () => ({
    todoText: "",
    todos: [],
    inputChecked: false,
  }),
  methods: {
    saveTodo() {
      if (!this.todoText) {
        return
      }  
      console.log({ todoText: this.todoText, isChecked: this.inputChecked });
      this.todos.push({
        todoText: this.todoText,
        isChecked: this.inputChecked,
      });
      this.todoText = "";
      this.inputChecked = false;
    },
    check(val) {
      this.inputChecked = val;
    },
  },
  components: {
    Todo,
    GradCheckbox,
  },
};
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

.btn {
  @apply p-3 shadow outline-none text-white rounded-xl;
}
.btn:focus {
  @apply outline-none;
}

.btn-gradient {
  background: linear-gradient(45deg, hsl(192, 100%, 67%), hsl(280, 87%, 65%));
}

.container {
  @apply min-h-screen flex justify-center items-center mx-auto;
}
</style>
