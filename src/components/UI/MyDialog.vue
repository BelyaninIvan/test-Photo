<template>
  <div 
    class="modal" 
    v-if="show === true" 
    @click.stop="hideDialog">
    <div 
      @click.stop
      class="modal__content"
    >
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MyDialog',
  props: {
    show: {
      type: Boolean,
      default: false,
    }
  },
  methods: {
    hideDialog() {
      this.$emit('update:show', false);
    }
  }
}
</script>

<style scoped>
  .modal {
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.4);
    position: fixed;
    display: flex;
  }

  .modal__content {
    margin: auto;
    background-color: rgb(65, 140, 110);
    border-radius: 20px;
    padding: 25px;
  }
</style>