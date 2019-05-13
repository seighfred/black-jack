<template>
  <div>
    <v-container>
      <span class="black--text" position="background-position: bottom 50px right 100px;">{{ getValue(card.value) }}</span>
      <v-layout>
        <v-img :src="getSuit(card.suit)" position="center"></v-img>
      </v-layout>
      <span class="black--text alignRight">{{ getValue(card.value) }}</span>
    </v-container>
  </div>
</template>

</<script>
export default {
  props: {
    card: {
      type: Object,
      required: true
    }
  },
  methods:{
    getSuit(value) {
      switch(value) {
        case 'c': return 'suits/clover.png'
        case 'd': return 'suits/diamond.png'
        case 's': return 'suits/spade.png'
        case 'h': return 'suits/heart.png'
      }
    },
    getValue(value) {
      switch(value) {
        case 1: return 'A'
        case 11: return 'J'
        case 12: return 'Q'
        case 13: return 'K'
        default: return value
      }
    }
  }
}
</script>

<style>
.alignRight {
  float: right
}
.alignLeft {
  float: left
}
</style>

