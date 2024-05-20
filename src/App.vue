<template>
  <nav class="mainNav">
    <router-link to="/">things to do</router-link>
    <router-link to="/addTask">add task</router-link>
  </nav>
  <router-view/>
</template>
 
<style>

*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  background:ghostwhite;

}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  width: 100%;
  margin: 0px auto;
}

.mainNav{
  text-align: center;
  margin: 40px 0px;
}

.mainNav a{
  color: gray;
  font-size: 18px;
  margin: 0 10px;
  text-decoration: none;
}

a.router-link-active{
  border-bottom: 2px solid rgb(4, 187, 4);
  padding-bottom: 4px;
}
</style>
