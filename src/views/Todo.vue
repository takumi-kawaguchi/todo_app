<template>
  <div class="todo">
    <div class="container">
        <div class="row">
            <div class="col" v-for="(group, index) in taskGroups" :key="index">
                <div v-if="group.isGroupNameEditable">
                    <input type="text" v-model="group.groupName" @blur="changeStatus(group)">
                </div>
                <div v-else>
                    <p @click="changeStatus(group)">{{ group.groupName }}</p>
                </div>
                <input type="text" v-model="group.additionalTask"><button type="button" class="task-btn btn btn-outline-secondary btn-circle rounded-circle p-0" @click="addTask(group.additionalTask, index)">+</button>
                <draggable class="list-group" element="ul" :options="{ group: taskGroups }">
                    <li class="list-group-item" v-for="task in group.tasks" :key="task">{{ task }}</li>
                </draggable>
            </div>
            <div class="col"><button class="task-btn btn btn-outline-secondary" @click="addNewGroup">Click to add new task group</button></div>
        </div>

        <div class="debug">
            <p>{{ taskGroups }}</p>
        </div>
    </div>
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
                    groupName: '無名のグループ',
                    isGroupNameEditable: false,
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
        },
        addNewGroup: function() {
            this.taskGroups.push({
                groupName: '無名のグループ',
                additionalTask: '',
                tasks:[]
            });
        },
        makeGroupNameEditable: function(index) {
            var group = this.taskGroups[index];
            var newGroup = {
                groupName: group.groupName,
                isGroupNameEditable: true,
                additionalTask: group.additionalTask,
                tasks: group.tasks
            }
            this.$set(this.taskGroups, index, newGroup);
            // this.taskGroups.splice(index, 1, newGroup);
            console.log(this.taskGroups.length);
            for (const item of this.taskGroups) {
                console.log(item);
            }
            // this.$set(this.taskGroups, index, newGroup)
            // group.isGroupNameEditable = true;
        },
        changeStatus: function(group) {
            group.isGroupNameEditable = !group.isGroupNameEditable
            console.log(group.isGroupNameEditable);
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