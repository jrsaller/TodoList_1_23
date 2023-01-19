<script setup lang="ts">
    import { ref } from 'vue';
    const itemInput = ref('')
    const emit = defineEmits(['submitItem'])

    function submitItem(text: string) {
        emit('submitItem', text);
        itemInput.value = '';
    }
</script>

<template>
    <input type="text" name="itemInput" id="itemInput" v-model="itemInput">
    <button type="submit" @click="submitItem(itemInput)">Submit</button>
</template>