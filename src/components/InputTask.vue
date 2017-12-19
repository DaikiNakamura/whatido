<template>
  <div id="inputForm">
    <p class="error">{{ errorMessage }}</p>
    <input class="input" type="text" v-model="taskName"/>
    <select class="input" v-model="fromHour">
      <option v-for="n in 12">{{ ('0' + n).slice(-2) }}</option>
    </select>
    :
    <select class="input" v-model="fromMinute">
      <option>00</option>
      <option>30</option>
    </select>
    ～
    <select class="input" v-model="toHour">
      <option v-for="n in 12">{{ ('0' + n).slice(-2) }}</option>
    </select>
    :
    <select class="input" v-model="toMinute">
      <option>00</option>
      <option>30</option>
    </select>
    <button class="button" v-on:click="addTask">Add Task</button>
  </div>
</template>

<script>
  export default {
    name: 'InputForm',
    data: function () {
      return {
        taskName: '',
        fromHour: '09',
        fromMinute: '00',
        toHour: '10',
        toMinute: '00',
        errorMessage: ''
      }
    },
    methods: {
      addTask: function () {
        let from = this.fromHour + this.fromMinute
        let to = this.toHour + this.toMinute
        let color = '#' + Math.floor(Math.random() * 16777215).toString(16)
        this.$emit('set', {
          taskName: this.taskName,
          from: from,
          to: to,
          color: color
        })
        this.taskName = ''
      }
    }
  }
</script>


<style>
  .input {
    padding: 10px;
    font-size: 1.3em;
    font-family: Arial, sans-serif;
    color: #555;
    border: solid 1px #CCC;
    margin: 0 0 20px;
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;
    border-radius: 3px;
  }

  .input:focus {
    border: solid 1px #EEA34A;
  }

  .button {
    padding: 10px;
    font-size: 1.3em;
    font-family: Arial, sans-serif;
    color: #555;
    border: solid 1px #555;
    background-color: #CCC;
  }
  .button:hover {
    background-color: #555;
    color: #FFF;
  }
</style>
