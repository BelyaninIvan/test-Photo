<template>
  <main class="content">
    <CardsList
      status="Новые"
      buttonText="Хочу купить"
      :cardsList="cards"
      @move="moveCard"
      @delete="deleteCard"
      @openDialog="openDialog"
    >
    </CardsList>
    <CardsList
      status="Хочу купить"
      buttonText="Куплено"
      :cardsList="cards_favourites"
      @move="moveCardToBuy"
      @delete="deleteCard"
      class="list_work"
    >
    </CardsList>
    <CardsList 
      status="Уже купили"
      :cardsList="cards_buy"
      @delete="deleteCard"
      class="list_complete"
      isHide="true"
    >
    </CardsList>
  </main>

  <MyDialog
      :show="dialogVisible"
    >
      <CreateCardForm
        @create="createCard"
      >

      </CreateCardForm>
    </MyDialog>
</template>

<script>
  import axios from 'axios';
  import CardsList from '@/components/CardsList.vue';
  import CreateCardForm from '@/components/CreateCardForm.vue'
  export default {
    components: {
      CardsList,
      CreateCardForm
    },
    data() {
      return {
        cards: [],
        cards_favourites: [],
        cards_buy: [],
        dialogVisible: false,
      }
    },
    methods: {
      moveCard(card) {
        this.cards = this.cards.filter(c => c.id != card.id)
        this.cards_favourites.push(card);
      },
      moveCardToBuy(card) {
        this.cards_favourites = this.cards_favourites.filter(c => c.id != card.id)
        this.cards_buy.push(card);
      },
      deleteCard(card) {
        this.cards = this.cards.filter(c => c.id != card.id)
        this.cards_favourites = this.cards_favourites.filter(c => c.id != card.id)
        this.cards_buy = this.cards_buy.filter(c => c.id != card.id)
      },
      openDialog() {
        this.dialogVisible = true;
      },
      createCard(card) {
        this.cards.unshift(card);
        this.dialogVisible = false;
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
    justify-content: space-between;
  }
</style>
