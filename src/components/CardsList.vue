<template>
  <ul class="list">
    <button class="add-button" @click="$emit('openDialog')"></button>
    <h2 class="list__title">{{ status }} 
      <span class="list__title-span">{{ cardsList.length }}</span>
    </h2>
    
    <ListItem 
      v-for="card in cardsList"
      :key="card.id"
      :itemObj="card"
      @move="$emit('move', card)"
      @delete="$emit('delete', card)"
      :buttonText="buttonText"
      :isHide="isHide"
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
    },
    buttonText: {
      type: String,
      default: null
    },
    buttonType: {
      type: String,
      default: null
    },
    isHide: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      
    }
  },
  methods: {
    
  }
}
</script>
<style scoped>
  .list {
    position: relative;
    width: 400px;
    margin: 0;
    padding: 10px 20px;
    list-style-type: none;
    background-color: lightblue;
    border-radius: 40px;
    box-sizing: border-box;
    
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: top;
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

  .add-button {
    margin: 0;
    padding: 0;
    width: 24px;
    height: 24px;
    border: none;
    cursor: pointer;
    background-color: transparent;
    outline: none;
    background-image: url('../assets/add.png');
    background-size: 24px;

    position: absolute;
    right: 25px;
    top: 15px;
    transition: all ease-in .6s;
  }

  .add-button:hover {
    opacity: .8;
  }
</style>