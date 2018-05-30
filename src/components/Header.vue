<template>
  <nav class="navbar navbar-default">
    <div class="container-fluid">

      <div class="navbar-header">
        <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1">
          <span class="sr-only">Ouvrir la navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <a class="navbar-brand" href="/">Générateur de signature</a>
      </div>

      <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
        <ul class="nav navbar-nav">
          <li><a href="https://bde-efrei.fr/" target="_blank">BDE Overlord</a></li>
          <li><a href="http://efrei.fr/" target="_blank">Efrei Paris</a></li>
          <li><a href="https://github.com/bde-efrei-paris/signatures" target="_blank">GitHub du projet</a></li>
        </ul>

        <ul class="nav navbar-nav navbar-right">
          <li><a href="https://www.facebook.com/bdeoverlord/" target="_blank"><i class="fa fa-facebook" aria-hidden="true"></i></a></li>
          <li><a href="https://github.com/bde-efrei-paris" target="_blank"><i class="fa fa-github" aria-hidden="true"></i></a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
  export default {
    name: 'Header'
  }
</script>

<style>
  .fa {
    font-size: 150%;
  }
</style>
