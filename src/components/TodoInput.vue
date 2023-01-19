<script setup lang="ts">
    import { ref } from 'vue';
    import type { Ref } from 'vue';

    const itemInput: Ref<string> = ref('')

    // const emit = defineEmits(['submitItem'])
    const emit = defineEmits<{
        (e: 'submitItem',text: string) : void
    }>()

    function submitItem(text: string) : void {
        emit('submitItem', text);
        itemInput.value = '';
    }
</script>

<template>
    <input type="text" name="itemInput" id="itemInput" v-model="itemInput" @keyup.enter="submitItem(itemInput)">
    <button type="submit" @click="submitItem(itemInput)">Submit</button>
</template>