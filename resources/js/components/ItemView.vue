<template>
<div>
    <input type="checkbox" @change="updateStatus" v-model="item.completed" :true-value="1" :false-value="0"/>
    <span :class="[item.completed ? 'completed' :'notCompleted', 'itemName']">{{item.name}}</span>
    <button @click="deleteItem()">Delete</button>
</div>
</template>

<script>
export default {
    props:["item"],
    methods:{
        updateStatus(){
            axios.put('api/item/'+this.item.id, {
                item : this.item
            })
            .then( response =>{
                if ( response.status == 200){
                    this.$emit('statusChanged');
                }
            })
            .catch(error =>{
                console.log("Status Updating error")
            })
        },
        deleteItem(){
            axios.delete('api/item/'+this.item.id)
            .then( response =>{
                if ( response.status == 200){
                    console.log("try to emitting")
                    this.$emit('statusChanged')
                }
            })
            .catch(error =>{
                console.log("Error while deleting")
            })
        }
    },
    
}
</script>

<style>
.completed{
    text-decoration: line-through;
}
.notCompleted{
    text-decoration: none;
}

</style>