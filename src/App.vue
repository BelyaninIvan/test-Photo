<template>
  <main class="content">
    <CardsList
      status="Новые"
      buttonText="Хочу купить"
      :cardsList="cards"
      isAdd="true"
      @move="moveCard"
      @delete="deleteCard"
      @openDialog="openDialog"
      @openEditDialog="openEditDialog"
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

  <section>
    <MyDialog
      v-model:show="dialogVisible"
    >
      <CreateCardForm
        @create="createCard"
      >
      </CreateCardForm>
    </MyDialog>
    
    <MyDialog
      v-model:show="dialogEditVisible"
    >
      <EditCardForm
        @edit="editCard"
        :cardObj="activeCard"
      >
      </EditCardForm>
    </MyDialog>
  </section>
</template>

<script>
  import axios from 'axios';
  import CardsList from '@/components/CardsList.vue';
  import CreateCardForm from '@/components/CreateCardForm.vue';
  import EditCardForm from '@/components/EditCardForm.vue'
  export default {
    components: {
      CardsList,
      CreateCardForm,
      EditCardForm
    },
    data() {
      return {
        cards: [],
        cards_favourites: [],
        cards_buy: [],
        dialogVisible: false,
        dialogEditVisible: false,
        activeCard: {},
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
      openEditDialog(card) {
        this.activeCard = card;
        this.cards = this.cards.filter(c => c.id != card.id);
        this.dialogEditVisible = true;
      },
      createCard(card) {
        this.cards.unshift(card);
        this.dialogVisible = false;
      },
      editCard(card) {
        this.cards.unshift(card);
        this.dialogEditVisible = false;
      }
    },
    mounted() {
      axios.get(`https://fakestoreapi.com/products`)
      .then(res => {
        res.data.forEach(element => {
            this.cards.push(element);
        });
      })
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
