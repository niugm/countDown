<template>
  <div class="timer">
    <div class="title-block">
      <slot>
        <!--slot-->
      </slot>
    </div>
    <div class="column">
      <div class="block">
        <p class="digit">{{ days }}</p>
        <p class="text">Days</p>
      </div>
      <div class="block">
        <p class="digit">{{ hours }}</p>
        <p class="text">Hours</p>
      </div>
      <div class="block">
        <p class="digit">{{ minutes }}</p>
        <p class="text">Minutes</p>
      </div>
      <div class="block">
        <p class="digit">{{ seconds }}</p>
        <p class="text">Seconds</p>
      </div>
    </div>
  </div>
</template>
<style>
  .timer{
    background-color: #42b983;
    padding: 20px;
    margin: 20px;
  }
  .title-block{
    border: solid 1px #f2f2f2;
  }
  .title{
    font-size: 18px;
    font-weight: 700;
  }
  .timer .column .block{
    display: inline-block;
    margin: 0 10px;
    background-color: #FFF;
    padding: 10px;
  }
</style>
<script>
  export default {
    props: {
      date: {
        type: String
      }
    },
    data () {
      return {
        now: 0,
        count: 0
      }
    },
    methods: {
      loop () {
        this.count++
        this.now = Math.trunc(new Date().getTime() / 1000)
        console.log(this.now)
        console.log(this.count)
        this.count < 200 && setTimeout(this.loop, 1000)
      }
    },
    mounted () {
      this.loop()
    },
    computed: {
      seconds () {
        return (this.modifiedDate - this.now) % 60
      },
      minutes () {
        return Math.trunc((this.modifiedDate - this.now) / 60) % 60
      },
      hours () {
        return Math.trunc((this.modifiedDate - this.now) / 60 / 60) % 24
      },
      days () {
        return Math.trunc((this.modifiedDate - this.now) / 60 / 60 / 24)
      },
      modifiedDate: function () {
        return Math.trunc(Date.parse(this.date) / 1000)
      }
    }
  }
</script>
