<template>
    <div id="content">
        <h1>My Component</h1>
        <p>ชื่อ {{Name}} อายุ {{age}}</p>
    </div>
</template>


<script>

export default {
    
name: 'MyComponnent',
data() {
  return {
    Name:"BARAMEE",
    age: 20,
  }  
},       

}
</script>



<style scoped>

</style>