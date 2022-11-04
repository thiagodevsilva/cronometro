<template>
  <div id="app">
    <img alt="Cronômetro" class="img" src="./assets/cronometro.png">
    <a href="#" class="timer"> {{ numero }}</a>

    <div class="area-buttons">
      <button class="botao" @click="vai">{{ botao }}</button>
      <button class="botao" @click="limpar">LIMPAR</button>
    </div>

    <div class="list" v-show="historico.length > 0">
      <ul>
        <li v-for="item in historico" :key="item">Pausa em: {{ item }}</li>
      </ul>
      <button @click="historico = []">Limpar histórico</button>
    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
    numero: '00:00:00',
    botao: 'PLAY',
    timer: null,
    ss: 0,
    mm: 0,
    hh: 0,
    historico: []
    }
  },
  methods:{
    vai(){
      // alert('Clicou')
      if(this.timer !== null){
        //tem algo rodando
        clearInterval(this.timer);
        this.timer = null;
        this.botao = 'PLAY';
        if(this.ss != 0){
          this.historico.push(this.numero);
        }

      }else{
        //timer parado ou zerado
        this.timer = setInterval( () => {
          this.rodarTimer();
        }, 10) // 1 segundo == 1000 milisegundos
        this.botao = 'PAUSAR';
      }
    },
    limpar(){
      if(this.timer != null){
        clearInterval(this.timer);
        this.timer = null;
      }
      this.ss = 0;
      this.mm = 0;
      this.hh = 0;
      this.numero = '00:00:00';
      this.botao = 'PLAY';
      this.historico = [];
    },
    rodarTimer(){
      this.ss++;

      if(this.ss == 59) { 
        //deu 59 segundos
        this.ss = 0;
        this.mm++;
      }

      if(this.mm == 59){
        //chegou nos 59 minutos
        this.mm = 0;
        this.hh++;
      }

      let format = 
      (this.hh < 10 ? '0'+this.hh : this.hh) + ':' 
      + (this.mm < 10 ? '0'+this.mm : this.mm) + ':' 
      + (this.ss < 10 ? '0'+this.ss : this.ss);

      return this.numero = format;
      
    }
  }
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
  padding-top: 30px;
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
  font-size: 24px;
  border-radius: 5px;
  text-align: center;
  padding: 10px 0;
  margin: 0 10px;
  cursor: pointer;
  font-weight: bold;
  color: #FFFFFF;
}

.botao:hover{
  opacity: 0.85;
  transition: all 0.5s;
}

.list {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

ul{
  text-align: center;
  padding: 0;
}

ul li{
  margin-top: 4px;
  padding: 8px;
  background-color: #546e7a;
  list-style: none;
  font-size: 13px;
  border-radius: 5px;
  color: #FFFFFF;
  font-weight: 600;
}

.list button {
  cursor: pointer;
  border: 0;
  background-color: #ae4040;
  padding: 8px;
  border-radius: 5px;
  margin-bottom: 12px;
  font-weight: bold;
  color: #FFFFFF;
}

</style>
