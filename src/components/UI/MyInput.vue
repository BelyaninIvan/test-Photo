<template>
    <input type="text" class="input" :value="modelValue" @input="updateInput">
</template>

<script>
  export default {
    name: 'MyInput',
    props: {
      modelValue: [String, Number]
    },
    methods: {
      updateInput(event) {
        this.$emit('update:modelValue', event.target.value);
      }
    }
  }
</script>

<style>
    .input {
        margin: 0;
        padding: 0;
        border: 0;
        outline: none;
        width: 85%;

        padding: 10px 15px;
        background-color: rgba(240, 230, 140, 0.5);
        border-radius: 10px;

        font-size: 20px;
        font-weight: 700;
        color: white;
    }

    .input::placeholder {
        color: rgb(255, 255, 255);
        opacity: .6;
    }
</style>