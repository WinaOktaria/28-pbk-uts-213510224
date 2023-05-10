<template>
	<div id="nav">
		<router-link to="/">Home</router-link>
		<router-link :to="{ name: 'Todo' }">To Do List</router-link>
        <router-link :to="{ name: 'About' }">About</router-link>
        <router-link :to="{ name: 'contact' }">Contact Us</router-link>
        
    </div>
    
    <router-view></router-view>	
</template>
<style>

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    background-color: white;
}
#nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #333;
    color: #fff;
    padding: 20px;
  }
  #nav a {
    color: #fff;
    text-decoration: none;
    margin-right: 20px;
    font-weight: bold;
  }
  #nav a:hover {
  text-decoration: underline;
  background-color: grey;
}
</style>
