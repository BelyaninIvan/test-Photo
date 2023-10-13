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
    <button type="button" @click="createCard">
        Создать карточку
    </button>
  </form>
</template>
<script>
export default {
  name: 'CreateCardForm',
  data() {
    return {
      card: {
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
  },
  methods: {
    createCard() {
      this.card.id = Date.now();
      this.$emit('create', this.card);
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
</style>