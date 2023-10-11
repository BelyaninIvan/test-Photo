<template>
  <ul class="list">
    <h2 class="list__title">{{ status }} <span class="list__title-span">{{ cardsList.length }}</span></h2>
    
    <ListItem 
      v-for="card in cardsList"
      :key="card.id"
      :itemObj="card"
    >
    </ListItem>
  </ul>
</template>
<script>
import ListItem from '@/components/ListItem.vue'
export default {
  name: 'CardsList',
  components: {
    ListItem,
  },
  props: {
    cardsList: {
      type: Array,
    },
    status: {
      type: String,
      default: null
    }
  },
  data() {
    
  },
}
</script>
<style scoped>
  .list {
    max-width: 400px;
    margin: 0;
    padding: 10px 20px;
    list-style-type: none;
    background-color: lightblue;
    border-radius: 40px;
    box-sizing: border-box;
    
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    row-gap: 15px;
  }

  .list_complete {
    background-color: rgb(174, 230, 173);
  }

  .list_work {
    background-color: rgb(230, 173, 173);
  }

  .list__title {
    margin: 10px auto 0;
  }

  .list__title-span {
    border-radius: 50%;
    background-color: white;
    padding: 5px;
    color: darkgreen;
  }
</style>