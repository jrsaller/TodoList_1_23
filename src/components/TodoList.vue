<script setup lang="ts">
    import { reactive } from 'vue';

    import TodoInput from './TodoInput.vue';
    import TodoItem from './TodoItem.vue';

    let itemList: Array<string> = reactive([]);
    
    function addItem(text: string) : void{
        console.log('Add Item called');
        console.log(text);
        itemList.push(text);
        console.log(itemList);
    }

  function removeItem(index: number) : void {
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
        max-height:50vh;
        overflow-y: auto;
        outline:auto;
        outline-color: rgba(0, 0, 255, 0.24);
    }
    ul.no-bullets {
        list-style-type: none; /* Remove bullets */
        padding: 0; /* Remove padding */
        margin: 0; /* Remove margins */
    }
</style>