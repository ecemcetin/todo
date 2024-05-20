<template>
  <form @submit.prevent="handleSubmit">
    <label>Title</label>
    <input type="text" v-model="title" required>

    <label>Details</label>
    <textarea required v-model="details"></textarea>  

    <button>Edit</button>
  </form>
</template>

<script>
export default {
props:['id'],
data(){
  return{
    title:'',
    details:'',
    complete: false,
    uri:'http://localhost:3000/tasks/' + this.id
  }
},
mounted() {
     fetch(this.uri).then(res=>res.json()).then(data=>
     {
      this.title = data.title;
      this.details = data.details;
      this.complete=data.complete;
     }
     ).catch(err =>console.log(err.message))
   },
   methods:{
    handleSubmit(){
      fetch(this.uri,{method:'PUT',
             headers:{'Content-Type':'application/json'},
             body:JSON.stringify({title:this.title,details:this.details,complete:this.complete}) 
        }).then(()=> {
          this.$router.push('/')
        }).catch(err =>console.log(err.message))
    }
   }
}
</script>

<style>

</style>