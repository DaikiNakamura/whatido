<template>
  <div id="taskList">
    <ul>
      <li class="task" v-for="(task, index) in tasks">
        {{ task.taskName }}　({{ formatTaskTime(task.from) }} ～ {{ formatTaskTime(task.to) }})
        <button v-on:click="deleteTask(index)" class="deleteButton" :style="{ backgroundColor: task.color }">DELETE</button>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'TaskList',
    props: ['tasks'],
    methods: {
      formatTaskTime: function (time) {
        return time.substr(0, 2) + '：' + time.substr(2)
      },
      deleteTask: function (index) {
        this.tasks.splice(index, 1)
      }
    }
  }
</script>

<style>
  .deleteButton {
    border: 2px solid #000;
  }
  .task {
    font-size: 1.3em;
  }
</style>
