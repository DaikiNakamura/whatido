<template>
  <div id="app">
    <InputTask @set="addTask"/>
    <TaskList v-bind:tasks="tasks" />
    <Clock />
    <div class="visualTaskArea">
      <VisualTask v-for="task in tasks" v-bind:task="task" class="visualTask"/>
    </div>
  </div>
</template>

<script>
import InputTask from './components/InputTask'
import TaskList from './components/TaskList'
import Clock from './components/Clock'
import VisualTask from './components/VisualTask'

export default {
  name: 'app',
  components: {
    InputTask,
    TaskList,
    Clock,
    VisualTask
  },
  data: function () {
    return {
      tasks: []
    }
  },
  methods: {
    addTask: function (data) {
      this.tasks.push(data)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.visualTaskArea {
  position: relative;
  top: -500px;
  width: 500px;
  margin: 0 auto;
}
</style>
