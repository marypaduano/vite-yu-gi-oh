<template>
    <main class="main">
        <div class="container">
            <ul class="card">
                <li class="card" v-for="card in cards" :key="card.id">
                    <img :src="card.card_image.image_url" alt="">
                    <h3 class="card_archetype">{{ card.archetype }}</h3>
                </li>
            </ul>
        </div>
    </main>
</template>
  
<script>
import axios from 'axios'
import store from '../store'

export default {

    data() {
        return {
            cards: [],
            store,
        }
    },

    methods: {
        fetchCards() {
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then((res) => {
                    this.store.cards = res.data.data
                })
        }
    },
    created() {
        this.fetchCards()
    },
}
</script>