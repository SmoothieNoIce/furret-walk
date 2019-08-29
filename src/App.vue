<template>
  <div id="app">
    <div id="div-furret">
      <img id="img-furret"  draggable="true" src="./assets/furret.gif" />
    </div>
    <div id="div-function">
      <p style="margin-left: 20px;" class="mdc-theme--primary" type="button" id="btn-furret">he walk uwu</p>
      <button style="margin-left: 20px;" class="mdc-button mdc-theme--primary" type="button" id="btn-theme" v-on:click="changeBackground()">Background</button>
      <button style="margin-left: 20px;" class="mdc-button mdc-theme--primary" type="button" id="btn-github" v-on:click="goToGithub()">Github</button>
      <button style="margin-left: 20px;" class="mdc-button mdc-theme--primary" type="button" id="btn-music" v-on:click="stopMusic()">Disable music</button>
    </div>
    <audio id="aud-accumula" autoplay>   
       <source id="src-accumula" src="./assets/accumula-town.mp3"  />    
    </audio>
  </div>
</template>

<script>
export default {
  name: "app",
  data () {
    return {
        count:0
    }
  },
  mounted(){
    this.init();
  },
  methods: {
    init : function() {
      let audio = document.getElementById('aud-accumula');
      let elem = document.querySelector('#img-furret');
      var draggie = new Draggabilly( elem, {
        // options...
      });
      audio.play();
      audio.addEventListener('ended', function(){
          this.play();
      }, false);
    },
    goToGithub : function() {
      let url="https://github.com/SmoothieNoIce/furret-walk";
      window.open(url, '_blank');
      redirectWindow.location;
    },
    stopMusic : function() {
       let btn = document.getElementById('btn-music');
       let audio = document.getElementById('aud-accumula');
       if(audio.paused){
          audio.play();
          btn.innerHTML="disable music";
       }else{
          audio.pause();
          btn.innerHTML="enable music";
       }
    },
    changeBackground : function() {
      switch(this.count){
        case 0:
          document.body.style.background = "#121212";
          document.body.style.backgroundImage="";
          break;
        case 1:
          document.body.style.background = "#121212";
          document.body.style.backgroundImage = "url(https://i.imgur.com/EXiMZL3.png)"
          break; 
        case 2:
          document.body.style.background = "#121212";
          document.body.style.backgroundImage = "url(https://i.imgur.com/qHqMk8P.png)";
          break; 
        default:
          document.body.style.background = "#fafafa";
          document.body.style.backgroundImage="";
          break; 
      }
      this.count+=1;
      if(this.count>=4){
        this.count=0;
      }
    },
  }
};

</script>

<style>
:root {
  --mdc-theme-primary: #fcb8ab;
  --mdc-theme-secondary: #feeae6;
}
body {
  transition: background 1.5s;
  background: #ffffff fixed center center;
  -webkit-transition: background 2s;
  -moz-transition: background 2s;
  -ms-transition: background 2s;
  -o-transition: background 2s;
  transition: background 2s;
}
#img-furret{
  margin: 0 auto;
  width: 200px;
  height: 100px;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#div-furret{
    margin-top:18%;
}
#div-function{
  position: fixed;
  left: 49%;
  bottom: 0px;
  transform: translate(-50%, -50%);
  margin: 0 auto;
}
:root {
  --mdc-theme-primary: #A15E49 !important;
  --mdc-theme-on-primary: #ffffff !important;
}
</style>
