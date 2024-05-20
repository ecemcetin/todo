<template>
  <form @submit.prevent="handleSubmit">
    <label>Title</label>
    <input type="text" v-model="title" required>

    <label>Details</label>
    <textarea required v-model="details"></textarea>  

    <button>Add</button>
  </form>
</template>

<script>
export default {
  data(){
    return{
      title:'',
      details:'',
      uri:'http://localhost:3000/tasks'
    }
  },
  methods:{
    handleSubmit(){
      let task={
        id:Math.floor(Math.random()*100000),
        title:this.title,
        details:this.details,
        complete:false
      }
      fetch(this.uri,{method:'POST',
             headers:{'Content-Type':'application/json'},
             body:JSON.stringify(task) 
        }).then(()=>{this.$router.push('/')}).catch(err =>console.log(err.message))
    }
  }
}
</script>

<style>
form{
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  padding: 20px;
  border-radius: 10px;
  background: white;
}

input{
  width: 100%;
  border: none;
  border-bottom: 1px solid gray;
  outline: none;
}

textarea{
  border: 1px solid gray;
  outline: none;
  width:100%;
  height: 100px;
  border-radius: 20px;
  padding: 10px;
}

label{
margin: 20px 0 10px 0;
display: block;
color: gray;
font-size: 15px;
font-weight: 500;
letter-spacing: 1;
text-transform: uppercase;
}

button{
  padding: 10px 30px;
  font-size: 18px;
  background: green;
  color: white;
  border: none;
  border-radius: 20px;
  margin: 20px auto;
  display: block;
  cursor: pointer;
}
</style>