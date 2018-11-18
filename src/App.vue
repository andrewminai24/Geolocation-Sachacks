<template>
  <div id="app">
    <div class="label">Your Speed:</div>
    <div class="speed">{{location}}</div>
  </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld.vue'
    import {Plugins} from '@capacitor/core'
    const { Geolocation} = Plugins

    export default {
        name: 'app',
        data() {
            return {
                location: '0.0'
            }
        },
        components: {
            HelloWorld
        },
        mounted() {
            Geolocation.watchPosition({enableHighAccuracy:true}, (position, err) => {
                console.log(position)
                this.location = (position.coords.speed * 2.23694).toFixed(1)
            })
        }
    }
</script>

<style>
  .label {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    margin-top: 60px;
    font-size: 30px;
  }
  .speed {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    margin-top: 60px;
    font-size: 80px;
  }
</style>