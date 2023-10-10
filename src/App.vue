<template>
  <main class="content">
    <CardsList>

    </CardsList>
  </main>
</template>

<script>
  import CardsList from '@/components/CardsList.vue';
  export default {
    components: {
      CardsList,
    }
  }
</script>

<style scoped>
  .main {
    margin: 0 auto;
    max-width: 1440px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
</style>
