<template>
  <form class="form" @submit.prevent>
    <MyInput
      v-model="card.title" 
      type="text" 
      name="title" 
      placeholder="Название товара"  
    />
    <MyInput
      v-model="card.category" 
      type="text" 
      name="category" 
      placeholder="Категория товара"  
    />
    <MyInput
      v-model="card.image" 
      type="text" 
      name="image" 
      placeholder="Ссылка на фото товара"  
    />
    <MyInput
      v-model="card.description" 
      type="text" 
      name="description" 
      placeholder="Описание товара"  
    />
    <MyInput
      v-model="card.price" 
      type="text" 
      name="price" 
      placeholder="Цена товара"  
    />
    <MyInput
      v-model="card.rating.count" 
      type="text" 
      name="count" 
      placeholder="Количество отзывов"  
    />
    <MyInput
      v-model="card.rating.rate" 
      type="text" 
      name="rate" 
      placeholder="Оценка отзывов"  
    />
    <button class="button" type="button" @click="editCard">
        Сохранить карточку
    </button>
  </form>
</template>
<script>
export default {
  name: 'EditCardForm',
  data() {
    return {
      card: {
        title: 'Название',
        category: 'Название',
        image: 'Название',
        description: 'Название',
        price: 'Название',
        rating: {
            count: 'Название',
            rate: 'Название',
        },
      },
    }
  },
  props: {
    /* cardObj: {
      type: Object,
    } */
  },
  methods: {
    editCard() {
      this.$emit('edit', this.card);
      this.card = {
        title: '',
        category: '',
        image: '',
        description: '',
        price: '',
        rating: {
          count: '',
          rate: '',
        },
      }
    }
  }
}
</script>
<style scoped>
  .form {
    display: flex;
    flex-direction: column;
    row-gap: 15px;
  }

  .button {
    margin: 0;
    padding: 10px 15px;
    border: none;
    border-radius: 10px;
    background-color: rgb(150, 251, 210);

    font-size: 18px;
    font-weight: 700;
    cursor: pointer;
    transition: all ease-in .8s;
  }

  .button:hover {
    background-color: rgba(150, 251, 211, 0.6);
    color: rgb(84, 84, 84);
  }
</style>