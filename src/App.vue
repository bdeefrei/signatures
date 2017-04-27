<template>
  <div id="app">
    <app-header></app-header>
    <div class="container">
      <generator></generator>
    </div>
  </div>
</template>

<script>
import AppHeader from './components/Header'
import Generator from './components/Generator'

export default {
  name: 'app',
  components: {
    AppHeader,
    Generator
  }
}
</script>
