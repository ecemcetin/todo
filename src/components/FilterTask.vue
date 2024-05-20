<template>
  <nav class="filterNav">
    <button @click="updateFilter('all')" :class="{active:current === 'all'}">all</button>
    <button  @click="updateFilter('done')" :class="{active:current === 'done'}">done</button>
    <button  @click="updateFilter('inprogress')" :class="{active:current === 'inprogress'}">in progress</button>
  </nav>
</template>

<script>
export default {
  emits:[
    'filterChange'
  ],
  props:['current'],
methods:{
  updateFilter(filterValue){
    this.$emit('filterChange', filterValue)
  }
}
}
</script>

<style>
 .filterNav button{
    background: beige;
    color: gray;
    display: inline-block;
    margin-left: 20px;
    font-size: 15px;
    padding: 10px 15px;
  }

  .active{
    background: rgb(72, 114, 9) !important;
    color: white !important;
  }
</style>