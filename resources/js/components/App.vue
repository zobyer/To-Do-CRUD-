<template>
<div class="toDocontainer">
  <div class="toDo">
    <h2>To DO App</h2>
    <input-item v-on:updateResult="getItem()"/>
  </div>
  <item-list :items="items" v-on:updateResult="getItem()"/>
</div>
</template>

<script>
import inputItem from './inputItem.vue'
import ItemList from './itemList.vue'

export default {
  components: { inputItem, ItemList },
  data: function(){
    return{
      items:[]
    }
  },
  methods:{
    getItem(){
      axios.get('api/items')
      .then( response => {
        this.items = response.data
        console.log("getting all items")
      })
      .catch( error =>{
        console.log("Error getting all the item name")
      })
    }
  },

  created(){
    this.getItem()
  }
  
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