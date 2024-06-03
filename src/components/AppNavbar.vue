<template>
  <nav class="nav">
   
    <ul class="nav-list">
      <li class="nav-item">
        <button class="btn btn-header" @click="filterPokemons(null)">
          <span style="background-image: url('./img/pokemon.png'); width: 60px; height: 60px;"></span>
        </button>
      </li>
      <!-- Otros botones para tipos de Pokémon -->
      <li v-for="(type, index) in pokemonTypes" :key="index" class="nav-item">
        <button class="btn btn-header" :class="type" @click="filterPokemons(type)">
          {{ type }}
        </button>
      </li>
      <li class="nav-item">
        <button class="btn btn-header" @click="showAllPokemons">Ver todos</button>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      pokemonTypes: ['Normal', 'Fire', 'Water', 'Grass', 'Electric', 'Ice', 'Fighting', 'Poison', 'Ground', 'Flying', 'Psychic', 'Bug', 'Rock', 'Ghost', 'Dark', 'Dragon', 'Steel', 'Fairy']
    };
  },
  methods: {
    // Método para filtrar Pokémon por tipo o mostrar todos los Pokémon
    filterPokemons(type) {
      // Emitir un evento al componente padre (App.vue) con el tipo de Pokémon seleccionado o null para mostrar todos los Pokémon
      this.$emit('filter-pokemons', type);
    },
    // Método para mostrar todos los Pokémon
    showAllPokemons() {
      // Emitir un evento al componente padre (App.vue) para mostrar todos los Pokémon
      this.$emit('show-all-pokemons');
    }
  }
};
</script>

<style>
/* Estilos específicos para el navbar */
</style>
