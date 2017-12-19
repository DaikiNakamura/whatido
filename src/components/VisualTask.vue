<template>
  <svg width="500" height="500" viewBox="-250 -250 500 500" version="1.1" xmlns="http://www.w3.org/2000/svg">
    <path v-for="task in tasks" :d="d(task)" :fill="task.color" />
  </svg>
</template>

<script>
  export default {
    name: 'VisualTask',
    props: ['tasks'],
    data: function () {
      return {
        radius: 180, // 半径
        center: {
          x: 0,
          y: 0
        }
      }
    },
    computed: {
    },
    methods: {
      x1: function (sr) {
        return (this.center.x + this.radius) * Math.cos(sr)
      },
      y1: function (sr) {
        return (this.center.y + this.radius) * Math.sin(sr)
      },
      x2: function (er) {
        return (this.center.x + this.radius) * Math.cos(er)
      },
      y2: function (er) {
        return (this.center.y + this.radius) * Math.sin(er)
      },
      dx: function (sr, er) {
        return this.x2(er) - this.x1(sr)
      },
      dy: function (sr, er) {
        return this.y2(er) - this.y1(sr)
      },
      f: function (startAngle, endAngle) {
        return Math.abs(endAngle - startAngle) > 180 ? 1 : 0
      },
      d: function (task) {
        let startHour = parseInt(task.from.substr(0, 2))
        let startMinutes = parseInt(task.from.substr(2))
        let startAngle = (startHour * 30 - 90) + (30 / 60 * startMinutes)
        let sr = startAngle * Math.PI / 180
        startHour = startHour > parseInt(task.to.substr(0, 2)) ? parseInt(task.to.substr(0, 2)) + 12 : parseInt(task.to.substr(0, 2))
        console.log(startHour)
        startMinutes = parseInt(task.to.substr(2))
        let endAngle = (startHour * 30 - 90) + (30 / 60 * startMinutes)
        let er = endAngle * Math.PI / 180
        return 'M ' + this.center.x + ',' + this.center.y + ' ' +
          'L ' + this.x1(sr) + ',' + this.y1(sr) + ' ' +
          'a ' + this.radius + ' ' + this.radius + ' ' + startAngle + ' ' +
          this.f(startAngle, endAngle) + ',1 ' + this.dx(sr, er) + ',' + this.dy(sr, er) + ' z'
      }
    }
  }
</script>

<style scoped>

  .baseArea {
    position: absolute;
  }

  /*.taskObj {*/
    /*fill: #00F;*/
  /*}*/
  /*.taskObj:nth-child(2n) {*/
    /*fill: #F00;*/
  /*}*/

</style>
