<script setup lang="ts">
    const props = defineProps({
        itemText: String,
        index: Number
    })

    const emits = defineEmits(['removeItem'])


</script>

<template>
    <div class="item">
        <input type="checkbox" class="checkbox">
        <b>{{ itemText }}</b>
        <button class="removeButton" @click="emits('removeItem')">X</button>
    </div>
</template>

<style scoped>
    .item {
        height:5vh;
        background-color: lightblue;
        outline: auto;
        outline-color: blue;
        margin-top: 1%;
    }
    .checkbox {
        float: left;
        height:60%;
        width: 3%;
        margin-top:0.5%;
    }
    .removeButton {
        float:right;
    }
</style>