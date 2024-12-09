<template>
    <ul class="cards-container">
      <li v-for="card in cards" :key="card.id">
        <Card :cardText="card.cardText" :cardImage="card.cardImage" :route="card.route" />
      </li>
    </ul>
  </template>

  <script>
  import Card from './Card.vue';

  export default {
    components: {
      Card
    },
    data() {
      return {
        cards: [
          { id: 1, cardImage: '/images/golden_trophy.webp', cardText: 'Tournaments', route: '/tournaments' },
          { id: 2, cardImage: '/images/recent.jpg', cardText: 'Recent', route: '/recent' },
          { id: 3, cardImage: '/images/quiz.jpg', cardText: 'Quiz', route: '/quiz' },
          { id: 4, cardImage: '/images/plus.jpg', cardText: 'Create', route: '/create' }
        ]
      }
    }
  }
  </script>

  <style scoped>
  .cards-container {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: center;
    list-style: none;
    margin-bottom: 6vh;
    margin-top: 6vh;
  }
  </style>

