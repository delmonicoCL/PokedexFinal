<template>
  <div id="app">
    <Navbar />
    <main>
      <h1>Welcome to the Pokédex</h1>
      <p>Here you can find information about different Pokémon!</p>
      <GrillaPokemon />
    </main>
    <AppFooter />
  </div>
</template>

<script>
import navbar from './components/navbar.vue';
import grillaPokemon from './components/grillapokemon.vue';

export default {
  name: 'App',
  components: {
    navbar,
    grillaPokemon
  }
}
</script>

<style>
/* Estilos globales aquí */
</style>
