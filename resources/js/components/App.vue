<template>
<div class="toDocontainer">
  <div class="toDo">
    <h2>To DO App</h2>
    <input-item />
  </div>
  <item-list />
</div>
</template>

<script>
import inputItem from './inputItem.vue'
import ItemList from './itemList.vue'

export default {
  components: { inputItem, ItemList },
  
}
</script>

<style>
.toDocontainer{
  width: 350px;
  margin: auto;
}

.toDo{
  background: #e6e6e6;
  padding: 10px;
  text-align: center;
}

</style>