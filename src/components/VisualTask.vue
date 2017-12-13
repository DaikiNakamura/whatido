<template>
  <div id="baseArea" class="baseArea">
  </div>
</template>

<script>
  export default {
    name: 'VisualTask',
    props: ['task']
  }
</script>

<style scoped>

  .baseArea {
    position: absolute;
    height: 500px;
    width: 500px;
    border-radius: 50%;
    margin: 0 auto;
    background-color: red;
  }

</style>
