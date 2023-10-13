<script>
    export default {
        name: 'MyButton'
    }
</script>

<template>
    <button class="button" type="button">
        <slot></slot>
    </button>
</template>

<style scoped>
    .button {
        margin: 0;
        padding: 0;
        border: 0;
        outline: none;

        padding: 15px 20px;
        background-color: rgba(240, 230, 140, 0.5);
        border-radius: 10px;

        font-size: 20px;
        font-weight: 700;
        color: white;

        cursor: pointer;
        transition: all ease-in .7s;
    }

    .button:hover {
        opacity: .7;
        transform: translateY(-3px);
    }
</style>