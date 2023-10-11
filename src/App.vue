<template>
  <main class="content">
    <CardsList
      status="Новые"
      :cardsList="cards"
    >
    </CardsList>
    <CardsList
      status="Хочу купить"
      :cardsList="cards"
      class="list_work"
    >
    </CardsList>
    <CardsList 
      status="Уже купили"
      :cardsList="cards"
      class="list_complete"
    >
    </CardsList>
  </main>
</template>

<script>
  import axios from 'axios';
  import CardsList from '@/components/CardsList.vue';
  export default {
    components: {
      CardsList,
    },
    data() {
      return {
        cards: [],
      }
    },
    mounted() {
      axios.get(`https://fakestoreapi.com/products`)
      .then(res => {
        res.data.forEach(element => {
            this.cards.push(element);
        });
      })
      console.log(this.cards);
    }
  }
</script>

<style scoped>
  .content {
    margin: 0 auto;
    max-width: 1440px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
</style>
