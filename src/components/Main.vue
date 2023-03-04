<template>
    <main class="main">
        <div class="container">
            <ul class="cards">                
                <GameCards v-for="element in store.cards" :key="element.id" :card="element" />
             
            </ul>
        </div>
    </main>
</template>

  
<script>
import axios from 'axios'
import store from '../store'
import GameCards from './GameCards.vue'

export default {
    components: {
      GameCards
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
            axios
                .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
                .then((res) => {                
                    this.store.cards = res.data.data
                    console.log(res.data.data)
                    
                })
        }
    },
    created() {
        this.fetchCards()
    },
}
console.log(store.image)
</script>

<style lang="scss" scoped>

.main{
    background-image: url('../img/wallpaper.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    padding-top: 80px;
}
.cards {
  display: grid;
  gap: 10px;
  grid-template-columns: repeat(6,1fr);
}
</style>