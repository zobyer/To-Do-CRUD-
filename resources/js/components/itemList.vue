<template>
<div v-for="(item, index) in items" :key="index">
    <item-view :item="item" v-on:statusChanged="$emit('updateResult')"/>
</div>
</template>

<script>
import ItemView from './ItemView.vue'
export default {
  components: { ItemView },
    props:["items"],
    
}
</script>

<style>

</style>