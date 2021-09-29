<template>
  <Countdown :targetDate="nextDate()"/>
</template>

<script>
import Countdown from './components/Countdown.vue'

export default {
  name: 'App',
  components: {
    Countdown
  },
  methods: {
    nextDate() {


        let string = "2021-09-24 17:00:00";
        let datum = new Date(string);
        return datum;
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
