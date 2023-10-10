<template>
  <div>
    <button class="button" type="button" @click="addCards">
      Добавить карточки
    </button>
    <ul class="list" >
      <li v-for="card in cards">
        <p>{{ card.title }}</p>
      </li>
    </ul>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  name: 'CardsList',
  data() {
    return {
      cards: [],
    }
  },
  methods: {
    addCards() {
      axios.get(`https://fakestoreapi.com/products`)
      .then(res => {
        res.data.forEach(element => {
            this.cards.push(element);
        });
      })
      console.log(this.cards);
    }
  }
}
</script>
<style scoped>
    
</style>