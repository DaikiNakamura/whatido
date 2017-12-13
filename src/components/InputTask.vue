<template>
  <div id="inputForm">
    <p class="error">{{ errorMessage }}</p>
    <input type="text" v-model="taskName"/>
    <select v-model="fromHour">
      <option v-for="n in 12">{{ ('0' + n).slice(-2) }}</option>
    </select>
    :
    <select v-model="fromMinute">
      <option v-for="n in 60">{{ ('0' + (n - 1)).slice(-2) }}</option>
    </select>
    ～
    <select v-model="toHour">
      <option v-for="n in 12">{{ ('0' + n).slice(-2) }}</option>
    </select>
    :
    <select v-model="toMinute">
      <option v-for="n in 60">{{ ('0' + (n - 1)).slice(-2) }}</option>
    </select>
    <button v-on:click="addTask">Add Task</button>
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
        let valid = this.isInRange(this.fromHour, this.fromMinute, this.toHour, this.toMinute)
        if (!valid) {
          return
        }
        let from = this.fromHour + this.fromMinute
        let to = this.toHour + this.toMinute
        this.$emit('set', {
          taskName: this.taskName,
          from: from,
          to: to
        })
        this.taskName = ''
      },
      isInRange: function (fromHour, fromMinute, toHour, toMinute) {
        let fromTotalMinute = parseInt(fromHour) * 60 + parseInt(fromMinute)
        let toTotalMinute = parseInt(toHour) * 60 + parseInt(toMinute)
        if (toTotalMinute - fromTotalMinute > 90) {
          this.errorMessage = '人間の集中力は90分しか持たないぜ・・・タスク分割してみよう！'
          return false
        } else {
          this.errorMessage = ''
        }
        return true
      }
    }
  }
</script>


<style>
.error {
  color: #F00;
  font-weight: bold;
}
</style>
