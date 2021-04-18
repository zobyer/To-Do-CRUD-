<template>
<div class="insert">
    <input type="text" v-model="item.name" placeholder="Enter anything...">
    <button @click="insert_in" :class="[item.name ? 'active': 'inactive', 'plus' ]">Submit</button>
</div>
</template>

<script>
export default {
    data: function(){
        return{
            item: {
                name:''
            }
        }
    },
    methods:{
        insert_in(){
            if ( this.item.name != ''){
                axios.post('api/item/store',{
                item: this.item
                })
                .then( response =>{
                    if( response.status == 201){
                        this.item.name =''
                        console.log("Item Inserted Succesfully")
                        this.$emit('updateResult')
                    }
                })
                .catch( error =>{
                    console.log("Item Inserting error")
                })
            }else{
                console.warn('insert something')
            }
        }
    }
}
</script>

<style>
.insert{
    display: flex;
    justify-content: center;
    align-items: center;
}
.insert input{
    background: #f7f7f7;
    border: 0px;
    border-radius: 10px;
    outline: none;
    padding: 5px;
    margin-right: 10px;
    width: 100%;
}

.plus{
    height: 25px;
    border: none;
    color: white;

}

.active{
    background: green;
    color: white;
    border: none;
    
}
.inactive{
    background: tomato;
}


</style>