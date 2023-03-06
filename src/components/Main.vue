<template>
    <main class="main">
        <div class="container">
            <Filters @onSearch="fetchCards" />
        </div>
        <div class="container">
            <ul v-if="store.cards.length > 0" class="cards">
                <GameCards v-for="element in store.cards" :key="element.id" :card="element" />
            </ul>
            <div v-else style="font-weight: 600;">
                Nessun risultato
            </div>
        </div>
    </main>
</template>

  
<script>
import axios from 'axios'
import store from '../store'
import GameCards from './GameCards.vue'
import Filters from './Filters.vue'

export default {
    components: {
        GameCards,
        Filters
    },

    data() {
        return {
            cards: [],
            store: store
        }
    },
    computed: {
        cardsGame() {
            return this.store.cards
        }
    },

    methods: {
        fetchCards() {
            const search = this.store.search
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0', {
                    params: {
                        fname: search,
                    }
                }).then((res) => {
                    this.store.cards = res.data.data
                }).catch((error) => {
                    this.store.cards = [];
                })
        }
    },
    created() {
        this.fetchCards()
    },
}
</script>

<style lang="scss" scoped>
.main {
    background-image: url('../img/wallpaper.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    padding: 80px 0;
}

.cards {
    display: grid;
    gap: 10px;
    grid-template-columns: repeat(5, 1fr);
}
</style>