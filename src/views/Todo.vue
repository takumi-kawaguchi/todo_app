<template>
  <div class="todo">
    <div class="container">
        <div class="row">
            <div class="col" v-for="(group, index) in taskGroups" :key="group">
                <input type="text" v-model="group.additionalTask"><button type="button" class="task-btn btn btn-outline-secondary btn-circle rounded-circle p-0" @click="addTask(group.additionalTask, index)">+</button>
                <draggable class="list-group" element="ul" :options="{ group: taskGroups }">
                    <li class="list-group-item" v-for="task in group.tasks" :key="task">{{ task }}</li>
                </draggable>
            </div>
        </div>
    </div>
    <!-- test -->
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
        taskGroups: [
            {
                additionalTask: '',
                tasks: []
            }
        ]
    }
    },
    methods: {
        addTask: function(taskName, index) {
            if (taskName.length > 0) {
                this.taskGroups[index].tasks.push(taskName);
                this.taskGroups[index].additionalTask = '';
            }

        }
    }
}
</script>

<style>
.task-btn {
    margin: 5px;
}

.btn-circle {
    width: 2em;
    height: 2em;
}
</style>