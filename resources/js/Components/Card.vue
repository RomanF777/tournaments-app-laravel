<template>
  <div class="card" @click="handleClick" style="cursor: pointer;">
    <div class="card_image">
      <img :src="cardImage" :alt="cardText" />
    </div>
    <div class="card_text">
      <h2>{{ cardText }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cardText: String,
    cardImage: String,
    route: String
  },
  created() {
    console.log(this.cardImage);
  },
  methods: {
    handleClick() {
      this.$router.push(this.route); // Use Vue Router to navigate
    }
  }
}
</script>

<style scoped>
.card {
  width: 300px;
  height: 360px;
  border: 1px solid #ddd;
  overflow: hidden;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s ease-in-out;
  margin: 10px;
  cursor: pointer;
  --angle: 0deg;
  border: 2vmin solid;
  border-image: conic-gradient(from var(--angle), red, yellow, lime, aqua, blue, magenta, red) 1;
  animation: 10s rotate linear infinite;
}

.card:hover {
  transform: scale(1.05);
}

.card_image img {
  display: block;
  width: 100%;
  height: 280px;
}

.card_text {
  padding: 10%;
  text-align: center;
  background-color: gold;
}

.card_text h2 {
  margin: 0;
  font-size: 1.5em;
  color: #333;
}
</style>
