<template>
  <div id="app">
    <!-- <AppNavbar @filter-pokemons="filterByType" @show-all-pokemons="showAllPokemons" /> -->
    <main>
      <div class="d-flex flex-column align-items-center justify-content-center mb-4">
        <img src="./assets/img/pokemon.png" alt="">
        <h1>Bienvenido a tu Pokédex</h1>
        <p>Conoce y selecciona tus Pokemon Favoritos :)</p>
      </div>
      <PokemonGrid :filteredType="filteredType" />
    </main>
  </div>
</template>

<script>
// import AppNavbar from './components/AppNavbar.vue';
import PokemonGrid from './components/PokemonGrid.vue';

export default {
  name: 'App',
  components: {
    // AppNavbar,
    PokemonGrid
  },
  data() {
    return {
      filteredType: null
    };
  },
  methods: {
    filterByType(type) {
      // Actualiza el tipo de filtro
      this.filteredType = type;
    },
    showAllPokemons() {
      // Restablece el tipo de filtro a null para mostrar todos los Pokémon
      this.filteredType = null;
    }
  }
};
</script>

<style>
</style>