<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import draggable from "vuedraggable"
export default {
  name: "app",
  components: {
    draggable
  },
  data() {
    return {
      tasks: [
        ['task1-1', 'task1-2', 'task1-3', 'task1-4', 'task1-5'],
        ['task2-1', 'task2-2', 'task2-3', 'task2-4', 'task2-5'],
        ['task3-1', 'task3-2', 'task3-3', 'task3-4', 'task3-5']
      ]
    }
  }
}
</script>
