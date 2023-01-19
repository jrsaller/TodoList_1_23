<script setup lang="ts">
  import TodoList from './components/TodoList.vue';
</script>

<template>
  <main>
    <h1>Default Slots</h1>
    <TodoList/>
    
    <h1>Custom Slots</h1>
    <TodoList v-slot="slotProps">
      <div class="slot-item">
        <input type="checkbox" name="customCheckbox" class="customCheckbox">
         {{ slotProps.text }}
        <button class="customRemoveButton" @click="slotProps.removeItem(slotProps.index)">X</button>
      </div>
    </TodoList>

  </main>
</template>

<style scoped>
  .slot-item {
        height:5vh;
        background-color: rgb(250, 231, 210);
        outline: auto;
        outline-color: rgb(162, 0, 255);
        margin-bottom: 1%;
    }
    .customCheckbox {
      float:left;
      height:60%;
      width: 3%;
      margin-top:0.5%;
    }
    .customRemoveButton {
      float:right;
    }

</style>
