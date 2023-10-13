<template>
  <li class="list__item item">
    <button class="del-button" @click="$emit('delete', itemObj)"></button>
    <h3 class="item__title">{{ itemObj.title }}</h3>
    <p class="item__category"> Категория: <span>{{ itemObj.category }}</span></p>
    <img class="item__image" :src="itemObj.image" alt="Картинка">
    <p class="item__text"> Описание: <span>{{ itemObj.description }}</span></p>
    <p class="item__category"> Цена: <span>{{ itemObj.price }}</span></p>
    <p class="item__category"> Количество отзывов: <span>{{ itemObj.rating.count }}</span></p>
    <p class="item__category"> Рейтинг: <span>{{ itemObj.rating.rate }}</span></p>
    <button class="button" :class="{ button_hide: isHide }" type="button" @click="$emit('move', itemObj)">{{ buttonText }}</button>
  </li>
</template>
<script>
export default {
  name: 'ListItem',
  props: {
    itemObj: {
      type: Object,
      default: null,
    },
    buttonText: {
      type: String,
    },
    buttonType: {
      type: String,
    },
    isHide: {
      type: Boolean,
      default: false
    }
  }
}
</script>
<style scoped>
  .list__item {
    position: relative;
    margin: 0;
    min-width: 330px;
    padding: 40px 15px 10px;
    background-color: white;
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    row-gap: 10px;
  }

  .del-button {
    margin: 0;
    padding: 0;
    width: 24px;
    height: 24px;
    border: none;
    cursor: pointer;
    background-color: transparent;
    outline: none;
    background-image: url('../assets/delete-button.png');
    background-size: 24px;

    position: absolute;
    top: 10px;
    right: 15px;
    transition: all ease-in .6s;
  }

  .del-button:hover {
    opacity: .8;
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
    text-align: center;
    font-weight: 600;
  }

  .item__text span {
    font-weight: 400;
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

  .button_hide {
    display: none;
  }

  .button:hover {
    background-color: rgba(150, 251, 211, 0.6);
    color: rgb(84, 84, 84);
  }
</style>