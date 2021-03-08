<template>
  <div id="root">
    <img alt="Vue logo" src="./assets/logo.png" />
    <div v-for="c in state.targets" :key="c.name">
    <h2 :class="{'text-danger': c.health == 0}">{{ c.name }}</h2>
    <h3 class="text-success" :class="{'text-danger': c.health < 40, 'text-warning': c.health < 80}">{{ c.health }}</h3>
    <button class="btn btn-danger" @click="c.health -= 10" :disabled="c.health < 10">Slap</button>
    <button class="btn btn-success" @click="c.health += 10" :disabled="c.health == c.max_health">Heal</button>
    </div>
  </div>
</template>

<script>
import { reactive } from 'vue'
export default {
  name: 'App',
  setup () {
    const state = reactive({
      targets: [
        {
          name: 'Master Evil Boss',
          health: 100,
          max_health: 100
        },
        {
          name: 'Evil Grunt Dude',
          health: 90,
          max_health: 90
        }
      ]
    })
    return {
      state
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
