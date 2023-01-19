<script setup lang="ts">
    import { reactive } from 'vue';

    import TodoInput from './TodoInput.vue';
    import TodoItem from './TodoItem.vue';
    const props = defineProps({
        itemList: Array<string>
    })
    const emits = defineEmits(['removeItem'])

    let itemList: Array<string> = reactive([]);
    function addItem(text: string) {
    console.log('Add Item called');
    console.log(text);
    itemList.push(text);
    console.log(itemList);
  }

  function removeItem(index: number) {
    console.log('remove Item called with index ',index)
    console.log('Before:', itemList)
    itemList.splice(index,1);
    console.log('After:',itemList)
  }

</script>

<template>
    <TodoInput @submit-item="addItem"/>
    <div class="list">
        <p v-if="!itemList || itemList.length == 0"> Start entering items!</p>
        <ul v-else class="no-bullets" v-for="(item,index) in itemList">
            <li>
                <slot :text="item" :index="index" :removeItem="removeItem">
                    <TodoItem :itemText="item"  @removeItem="removeItem(index)" />
                </slot>
            </li>
        </ul>
    </div>
</template>

<style scoped> 
    .list {
        width:80vw;
        height:50vh;
        outline:auto;
        outline-color: blue;
    }
    ul.no-bullets {
        list-style-type: none; /* Remove bullets */
        padding: 0; /* Remove padding */
        margin: 0; /* Remove margins */
    }
</style>