<template>
    <div>
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
                    <img class="favStar" src="./img/star.png" alt="">
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

main {
    padding: 2rem;
    max-width: 1000px;
    margin: 0 auto;
}

.pokemon-todos {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
}

@media screen and (min-width: 470px) {
    .pokemon-todos {
        grid-template-columns: 1fr 1fr;
    }
}

@media screen and (min-width: 700px) {
    .pokemon-todos {
        grid-template-columns: 1fr 1fr 1fr;
    }
}

.pokemon {
    border-radius: 1rem;
    background-color: var(--type-electric);
    box-shadow: 0 0 3rem -1rem rgba(0, 0, 0, .25);
    padding-block: 1rem;
    text-transform: uppercase;
    position: relative;
    isolation: isolate;
    overflow: hidden;
}

.pokemon-id-back {
    position: absolute;
    top: 1rem;
    left: 50%;
    transform: translateX(-50%);
    font-size: 6rem;
    font-weight: 800;
    z-index: -1;
    color: var(--clr-gray);
}

.pokemon-imagen {
    padding-inline: 1rem;
    display: flex;
    justify-content: center;
}

.pokemon-imagen img {
    width: 100%;
    max-width: 6rem;
    transition: transform 0.3s ease;
    /* Añade una transición suave para el efecto hover */
}

/* Efecto hover para agrandar la imagen */
.pokemon-imagen:hover img {
    transform: scale(1.5);
    /* Agranda la imagen al 110% */
}

.favStar {
    width: 4rem;
}

.pokemon-info {
    display: flex;
    flex-direction: column;
    gap: .5rem;
    padding-inline: 1rem;
    align-items: center;
    text-align: center;
}

.nombre-contenedor {
    display: flex;
    align-items: center;
    column-gap: .5rem;
    flex-wrap: wrap;
    justify-content: center;
}

.pokemon-id {
    background-color: var(--clr-gray);
    padding: .25rem .5rem;
    border-radius: 100vmax;
    font-size: .75rem;
    font-weight: 500;
}

.pokemon-nombre {
    font-size: 1.4rem;
}

.pokemon-tipos {
    display: flex;
    gap: .5rem;
    font-size: .75rem;
    font-weight: 500;
    flex-wrap: wrap;
    justify-content: center;
}

.tipo {
    padding: .25rem .5rem;
    border-radius: 100vmax;
}

.pokemon-stats {
    display: flex;
    gap: 1rem;
    font-size: .85rem;
}

.stat {
    background-color: var(--clr-gray);
    padding: .25rem .5rem;
    border-radius: 100vmax;
}



.normal {
    background-color: var(--type-normal);
    color: var(--clr-black);
}

.fire {
    background-color: var(--type-fire);
    color: var(--clr-black);
}

.water {
    background-color: var(--type-water);
    color: var(--clr-white);
}

.grass {
    background-color: var(--type-grass);
    color: var(--clr-black);
}

</style>
