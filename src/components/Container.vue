<template>
  <div class="container">
    <input
      type="text"
      v-model="msg"
    >
    <button @click="Create">Create</button>
    <TodoList
      :TodoLists="TodoLists"
      :Delete="Delete"
    />
  </div>
</template>

<script>
import TodoList from './TodoList';
import { ref } from "@vue/runtime-core";
export default {
  components: {
    TodoList,
  },
  setup() {
    let exampleData = [
      { id: 1, name: 'cooking' },
      { id: 2, name: 'eating' },
      { id: 3, name: 'dancing' },
    ];
    
    const Create = () => {
      let id = 4;
      id += 1;
      const next = { id, name: this.msg };
      this.TodoLists.push(next);
    }
    
    const Delete = (idx) => {
      this.TodoLists = this.TodoLists.filter((r) => r.id !== idx);
    }
    
    return {
      TodoLists: ref(exampleData),
      Create,
      Delete: Delete(idx)
    };
  }
}
</script>