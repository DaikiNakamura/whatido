<template>
  <div id="clock" class="clock">
    <span v-for="n in 12">{{ n }}</span>
    <div class="hour-hand"></div>
  </div>
</template>

<script>
  export default {
    name: 'Clock',
    mounted: function () {
      let hourFromDeg = (new Date().getHours() * 30 - 90) + (30 / 60 * new Date().getMinutes())
      let hourToDeg = hourFromDeg + 360
      let hourHandAnime = document.createElement('style')
      hourHandAnime.innerHTML = '@keyframes tick{0%{transform: rotate(' + hourFromDeg + 'deg);} 100%{transform: rotate(' + hourToDeg + 'deg);}}'
      document.head.appendChild(hourHandAnime)
    }
  }
</script>

<style scoped>

  .clock {
    position: relative;
    height: 500px;
    width: 500px;
    border-radius: 50%;
    margin: 0 auto;
    background-color: #EAEAEA;
  }

  .hour-hand {
    position: absolute;
    left: 50%;
    top: 50%;
    width: 180px;
    height: 3px;
    background-color: #000;
    transform-origin: left top;
    transform: rotate(40deg);
    animation: tick 43200s infinite linear;
    z-index: 9999;
  }

  .clock span {
    position: absolute;
    font-size: 2em;
    width: 45px;
    line-height: 1em;
    text-align: center;
    left: 50%;
    top: 50%;
    transform-origin: left top;
  }

  .clock span:nth-of-type(1) {
    transform: rotate(30deg) translate(0, -210px) rotate(-30deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(2) {
    transform: rotate(60deg) translate(0, -210px) rotate(-60deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(3) {
    transform: rotate(90deg) translate(0, -210px) rotate(-90deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(4) {
    transform: rotate(120deg) translate(0, -210px) rotate(-120deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(5) {
    transform: rotate(150deg) translate(0, -210px) rotate(-150deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(6) {
    transform: rotate(180deg) translate(0, -210px) rotate(-180deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(7) {
    transform: rotate(210deg) translate(0, -210px) rotate(-210deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(8) {
    transform: rotate(240deg) translate(0, -210px) rotate(-240deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(9) {
    transform: rotate(270deg) translate(0, -210px) rotate(-270deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(10) {
    transform: rotate(300deg) translate(0, -210px) rotate(-300deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(11) {
    transform: rotate(330deg) translate(0, -210px) rotate(-330deg) translate(-50%, -50%);
  }

  .clock span:nth-of-type(12) {
    transform: translate(0, -210px) translate(-50%, -50%);
  }

</style>
