<template>
  <div id="app">
      <div class="container">
        <div class="row">
          <div class="col-md-6 col-md-offset-3">
            <cityFinder></cityFinder>
          </div> 
        </div>
        <aside>
          <p>by Lucy Zidour</p>
        </aside>
      </div> 
  </div>
</template>

<script>

import cityFinder from './components/cityFinder'
export default {
  name: 'app',
  components: {
    cityFinder
  }
}

</script>

<style>

  #app {
    height: 100vh;
    width: 100vw;
    background-color: #ccc;
    background: url("https://source.unsplash.com/category/nature/1920x1080") no-repeat center center fixed;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
  }

  aside p {
    color: #fff;
    font-size: 16px;
    position: absolute;
    bottom: 10px;
  }

</style>
