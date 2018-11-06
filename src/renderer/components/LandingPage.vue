<template>
  <div id="wrapper">
    <img id="logo" src="~@/assets/схема.png" >
    <main>
      <div class="info">
        <div class="doc">
          <div class="title">Лабораторная работа 2</div>
          <p>
          Программа для управления реверсивным электроприводом ворот для проезда транспорта с электродвигателем трехфазного переменного тока.
          </p>
          <a class="gradient-btn" href="#/main">Начать</a>
          <!-- <img id="git" src="~@/assets/github.png" @onclick="github()" width="200"> -->
        </div>
      </div>
    </main>
  </div>
</template>

<script>
  export default {
    name: 'landing-page',
    methods: {
      open (link) {
        this.$electron.shell.openExternal(link)
      }
   }  
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body { font-family: 'Source Sans Pro', sans-serif; }
.info{
  margin-left: 200px;
  margin-top: 200px;
}
  #wrapper {
    background:
      radial-gradient(
        ellipse at top left,
        rgba(255, 255, 255, 1) 40%,
        rgba(229, 229, 229, .9) 100%
      );
    height: 100vh;
    padding: 60px 80px;
    width: 100vw;
  }

  #logo {
    height: auto;
    margin-bottom: 20px;
    width: 600px;
  }

  main {
    display: flex;
    justify-content: space-between;
  }

  main > div { flex-basis: 50%; }

  .left-side {
    display: flex;
    flex-direction: column;
  }

  .welcome {
    color: #555;
    font-size: 23px;
    margin-bottom: 10px;
  }

  .title {
    color: #2c3e50;
    font-size: 20px;
    font-weight: bold;
    margin-bottom: 6px;
  }

  .title.alt {
    font-size: 18px;
    margin-bottom: 10px;
  }

  .doc p {
    color: black;
    margin-bottom: 10px;
  }

  .doc button {
    font-size: .8em;
    cursor: pointer;
    outline: none;
    padding: 0.75em 2em;
    border-radius: 2em;
    display: inline-block;
    color: #fff;
    background-color: #4fc08d;
    transition: all 0.15s ease;
    box-sizing: border-box;
    border: 1px solid #4fc08d;
  }

  .doc button.alt {
    color: #42b983;
    background-color: transparent;
  }
.gradient-btn {
  position: absolute;
  top: 50%;
  left: 70%;
  transform: translate(-50%, -50%);
  width: 180px;
  height: 60px;
  text-align: center;
  line-height: 60px;
  font-family: sans-serif;
  font-size: 24px;
  color: #fff;
  text-transform: uppercase;
  text-decoration: none;
  letter-spacing: 6px;
  transition: .5s;
  background-color: aqua;
  border: 4px solid #fff;
  border-radius: 60px;
  box-shadow: 0 5px 20px rgba(0,0,0, .5);
  overflow: hidden;
}
.gradient-btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to left, #1366ff, #ff0b6d);
  z-index: -1;
  border-radius: 60px;
  transform: scaleX(0);
  transform-origin: right;
  transition: transform .5s ease-in-out;
}
.gradient-btn:hover::before {
  transform: scaleX(1);
  transform-origin: left;
}
</style>
