<script setup>
  import Scene from './components/Scene.vue'
  import Configuration from './components/Configuration.vue'
</script>

<template>
  <div class="navigation">
    <div class="logo"><span>VRKSpace&nbsp;</span><sup>[vɛʁkspeɪs]</sup></div>
    <div class="links">
        <a href="https://github.com/cybergaukler/vrkspace/wiki" target="_blank"><i class="fab fa-github-square"></i>&nbsp;Philosophy&More</a>
    </div>
  </div>
  <div class="scene">
    <Scene />
  </div>
  <Configuration class="configuration"/>
</template>

<style>
  body, html {
    position: relative;    
    height: 100%;
    margin: 0 auto;
  }
  .navigation {
    position: absolute;
    z-index:2;
    width:100%;
    height: 2em;
    font-size: 1em;
    left:0;
    padding: 0.2em;
    background-color: #555555;
    color: #a0a0a0;
  }
  .navigation .logo {
    float: left;
    margin-left:0.2em;
  }
  .navigation .logo span{
      font-weight: bold;
      color: #F8F8F8;
  }
  .navigation .links {
      float: right;
      margin-right: 8em;
  }
  .navigation .links a {
      display: block;
      float: left;
      margin-left: 2em;
      color: orange;
  }
  .navigation .links a:hover {
      color: #F8F8F8;
  }

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    position:relative;
    height:100%;
  }
  .scene {
    height: 66%
    }
</style>
