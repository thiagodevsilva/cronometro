<template>
  <div id="app">
    <img alt="Cronômetro" class="img" src="./assets/cronometro.png">
    <a href="#" class="timer">00:00:00</a>

    <div class="area-buttons">
      <button class="botao">Play</button>
      <button class="botao">Limpar</button>

    </div>
  </div>
</template>

<script>


export default {
  name: 'App',

}
</script>

<style>
#app {
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.img {
  padding-top: 80px;
}

.timer {
  color: #000000;
  font-size: 45px;
  font-weight: bold;
  text-decoration: none;
  margin-top: -200px;
}

.area-buttons {
  margin-top: 170px;
}

.botao {
  user-select: none;
  width: 150px;
  background-color: #546e7a;
  border: none;
  font-size: 20px;
  border-radius: 5px;
  text-align: center;
  padding: 10px 0;
  margin: 0 10px;
  cursor: pointer;
}

.botao:hover{
  opacity: 0.85;
  transition: all 0.5s;
}
</style>
