<template>
  <li class="list__item item">
    <h3 class="item__title">{{ itemObj.title }}</h3>
    <p class="item__category"> Категория: <span>{{ itemObj.category }}</span></p>
    <img class="item__image" :src="itemObj.image" alt="Картинка">
    <p class="item__text"> Описание: <span>{{ itemObj.description }}</span></p>
    <p class="item__category"> Цена: <span>{{ itemObj.price }}</span></p>
    <p class="item__category"> Количество отзывов: <span>{{ itemObj.rating.count }}</span></p>
    <p class="item__category"> Рейтинг: <span>{{ itemObj.rating.rate }}</span></p>
    
  </li>
</template>
<script>
export default {
  name: 'ListItem',
  props: {
    itemObj: {
      type: Object,
      default: null
    }
  }
}
</script>
<style scoped>
  .list__item {
    margin: 0;
    padding: 10px 15px;
    background-color: white;
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    row-gap: 10px;
  }

  .item__title {
    margin: 0;
    text-align: center;
  }

  .item__category {
    margin: 0;
    text-align: center;
    font-weight: 600;
  }

  .item__category span {
    font-weight: 400;
  }

  .item__image {
    width: 150px;
    object-fit: cover;
    display: block;
    margin: 0 auto;
  }

  .item__text {
    margin: 0;
    text-align: justify;
    font-weight: 600;
  }

  .item__text span {
    font-weight: 400;
  }
</style>