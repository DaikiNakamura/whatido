<template>
  <div id="taskList">
    <ul>
      <!--表ヘッダー-->
      <li class="task headerRow">
        <span class="taskName">Task</span>
        <span class="taskTime">Time</span>
        <span class="taskDeleteButton">Delete</span>
      </li>
      <!--タスクたち-->
      <li class="task" v-for="(task, index) in tasks">
        <span class="taskName">{{ task.taskName }}</span>
        <span class="taskTime">{{ formatTaskTime(task.from) }} ～ {{ formatTaskTime(task.to) }}</span>
        <span class="taskDeleteButton"><button v-on:click="deleteTask(index)" class="deleteButton" :style="{ backgroundColor: task.color }">DELETE</button></span>
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

  /* 表示形式 */
  #taskList ul {
    list-style: none;
    display: table;
  }
  #taskList li {
    display: table-row;
  }
  #taskList li span {
    display: table-cell;
  }
  #taskList li span.taskName {
    width: 300px;
    word-break: break-all;
  }
  #taskList li span.taskTime {
    width: 200px;
  }
  #taskList li span.taskDeleteButton {
    width: 100px;
  }
  #taskList .headerRow span {
    font-weight: bold;
  }

  /* 罫線 */
  #taskList li span {
    border-top: 1px solid #000;
    border-left: 1px solid #000;
  }
  #taskList li span:last-child {
    border-right: 1px solid #000;
  }
  #taskList li:last-child span {
    border-bottom: 1px solid #000;
  }

  /* 動き */
  #taskList li:not(.headerRow):hover {
    background-color: #cccccc;
  }
</style>
