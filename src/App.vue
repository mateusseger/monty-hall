<template>
  <div id="app">
    <h1>Problema de Monty Hall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="portsAmount">Quantas portas? </label>
        <input type="text" id="portsAmount" size="3"
          v-model.number="portsAmount">
        <hr>
        <label for="selectedPort">Qual porta é a premiada? </label>
        <input type="text" id="selectedPort" size="3"
          v-model.number="selectedPort">
        <hr>
        <button v-if="!started" @click="started = true">Iniciar</button>
      </div>
      <button v-if="started" @click="started = false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmount" :key="i">
        <Door :hasGift="i === selectedPort" :number="i"/>
      </div>
    </div>
  </div>
</template>

<script>
import Door from './components/Door'
export default {
  components: { Door },
  data() {
    return {
      started: false,
      portsAmount: 3,
      selectedPort: null
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}
body {
  color: #fff;
  background: linear-gradient(to right, rgb(21, 153, 87), rgb(21,87,153));
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
#app h1 {
  border: 1px solid #000;
  background-color: #0004;
  padding: 20px;
  padding-bottom: 60px;
}
.form {
  margin-bottom: 10px;
}
.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  margin: 15px;
}
</style>