<template>
  <div class="todo">
    <div class="container">
        <div class="row">
            <div class="col" v-for="list in tasks" :key="list">
                <draggable class="list-group" element="ul" :options="{ group: 'tasks' }">
                    <li class="list-group-item" v-for="item in list" :key="item">{{ item }}</li>
                </draggable>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
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