<template>
    <div class="pokemon-todos">
        <div v-for="poke in pokemons" :key="poke.id" class="pokemon">
            <p class="pokemon-id-back">#{{ formatId(poke.id) }}</p>
            <div class="pokemon-imagen">
                <img :src="poke.sprites.other['official-artwork'].front_default" :alt="poke.name">
            </div>
            <div class="pokemon-info">
                <div class="nombre-contenedor">
                    <p class="pokemon-id">#{{ formatId(poke.id) }}</p>
                    <h2 class="pokemon-nombre">{{ poke.name }}</h2>
                </div>
                <div class="pokemon-tipos">
                    <p v-for="type in poke.types" :key="type.type.name" :class="`${type.type.name} tipo`">
                        {{ type.type.name }}
                    </p>
                </div>
                <div class="pokemon-favoritos">
                    <img class="favStar" src="@/assets/img/star.png" alt="">
                </div>
                <div class="pokemon-stats">
                    <p class="stat">{{ poke.height }}m</p>
                    <p class="stat">{{ poke.weight }}kg</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            pokemons: [],
            URL: 'https://pokeapi.co/api/v2/pokemon/'
        };
    },
    methods: {
        fetchPokemons() {
            for (let i = 1; i <= 151; i++) {
                fetch(this.URL + i)
                    .then((response) => response.json())
                    .then((data) => {
                        this.pokemons.push(data);
                    });
            }
        },
        formatId(id) {
            let pokeId = id.toString();
            if (pokeId.length === 1) {
                return "00" + pokeId;
            } else if (pokeId.length === 2) {
                return "0" + pokeId;
            }
            return pokeId;
        }
    },
    mounted() {
        this.fetchPokemons();
    }
};
</script>

<style scoped>
/* Estilos específicos para los Pokémon */

</style>
