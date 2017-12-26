<template>
  <div id="app">
    <header>
      <img src="./assets/logo.png"/>
      <InputTask v-bind:tasks="tasks" @remove="removeTasks" />
      <hr />
    </header>
    <div class="contents">
      <div class="leftArea content">
        <div class="visualTaskArea">
          <Clock />
          <VisualTask v-bind:tasks="tasks" class="visualTask"/>
        </div>
      </div>
      <div class="rightArea content">
        <div class="taskDetailArea">
          <TaskList v-bind:tasks="tasks" />
        </div>
      </div>
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
    },
    removeTasks: function () {
      this.tasks = []
    }
  },
  created: function () {
    let dataFromUrlParam = JSON.parse(decodeURIComponent(document.location.search.substring(1)))
    this.tasks = dataFromUrlParam
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
  width: 500px;
  margin: 0 auto;
}
.visualTask {
  position: absolute;
  top: 0px;
  left: 0px;
}
.contents .content{
  display: inline-block;
}
.rightArea {
  margin-left: 20px;
  vertical-align: top;
}
</style>
