<template>
  <div>
    <v-container>
      <v-layout row wrap>
        <v-flex v-for="card in hand" :key="card.id" ma-2>
          <v-card
            class="rounded-card"
            color="white"
            min-height="200px"
            max-height="200px"
            min-width="140px"
            max-width="140px"
          >
            <cards :card="card"/>
          </v-card>
        </v-flex>
        <v-btn @click="getCard()">draw</v-btn>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
import cards from '@/components/cards'

export default {
  components: { cards },
  data() {
    return {
      deck: [],
      hand: []
    }
  },
  created() {
    this.initDeck(1)
    this.initCard()
  },
  methods: {
    initDeck(id) {
      ['c','d','h','s'].forEach(suit => {
        for(let i = 1; i <= 13; i++) {
          this.deck.push({ id: id, suit: suit, value: i })
          id++
        }
      })
    },
    initCard() {
      this.getCard()
      this.getCard()
    },
    getCard() {
      var card = {}
      var isDone = false
      var draw = null
      while(isDone !== true) {
        draw = Math.floor(Math.random() * 52)
        card = this.deck.find(card => card.id-1 == draw)
        isDone = card !== undefined ? true : false
      }
      this.hand.push(card)
      this.deck = this.deck.filter(card => card.id-1 !== draw)
    }
  }
}
</script>

<style>
.rounded-card{
    border-radius:10px;
}
</style>
