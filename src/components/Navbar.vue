<template>
   <div class="navbar">
       <h1>Việc cần làm</h1>
       <ul>
           <li>Home</li>
           <li>About</li>
       </ul>
   </div>
</template>

<script>
export default {
name: 'Navbar'
}
</script>

<style>
.navbar {
padding: 10px;
text-align: center;
background: #333;
color: #fff;
}
.navbar ul {
 display: flex;
 justify-content: space-around;
 align-items: center;
 list-style: none;
 padding: 0;
}
</style>