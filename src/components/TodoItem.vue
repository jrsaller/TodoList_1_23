<script setup lang="ts">
    import { ref } from 'vue';
    import type {Ref} from 'vue';

    let completed: Ref<boolean> = ref(false);

    // const props = defineProps({
    //     itemText: String,
    // })
    const props = defineProps<{
        itemText: String
    }>();

    // const emits = defineEmits(['removeItem'])
    const emits = defineEmits<{
        (e: 'removeItem'): void
    }>();

    function completeItem() : void {
        completed.value = !completed.value;
    }


</script>

<template>
    <div class="item">
        <input type="checkbox" class="checkbox" @change="completeItem">
        <div class="itemText" :class="(completed ? 'checked':'unchecked')">{{ props.itemText }}</div>
        <button class="removeButton" @click="emits('removeItem')">X</button>
    </div>
</template>

<style scoped>
    .item {
        min-height:5vh;
        background-color: lightblue;
        outline: auto;
        outline-color: blue;
        margin-top: 1%;
        text-align: left;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .checkbox {
        margin-top:0.5%;
        height:3vh;
        width:3vh;
    }
    .itemText {
        overflow-wrap: break-word;
        max-width: 75%;
        display: inline-block;
        padding: 1em;
    }
    .checked {
        text-decoration: line-through;
    }
    .unchecked {
        font-weight: bold;
    }
    
</style>