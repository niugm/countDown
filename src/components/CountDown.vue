<template>
  <div id="slideshow">
    <Timer :date="date">
      <p class="title">KNHB</p>
      <p class="description">Sprint 1</p>
    </Timer>
    <Timer :date="date">
      <p class="title">MG de Jong</p>
      <p class="description">Sprint 2</p>
    </Timer>
    <Timer :date="date">
      <p class="title">ITIP</p>
      <p class="description">Sprint 3</p>
    </Timer>
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
  import Timer from './Timer'
  export default {
    components: {
      Timer
    },
    props: {
      date: {
        type: String
      }
    },
    data () {
      return {
        now: Math.trunc((new Date()).getTime() / 1000)
      }
    },
    mounted () {
      window.setInterval(() => {
        this.now = Math.trunc((new Date()).getTime() / 1000)
      }, 1000)
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
