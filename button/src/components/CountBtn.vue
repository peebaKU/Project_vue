<template>
    <div>
      <button @click="greeting('Hello')" >Hello</button>
      <button @click="greeting('สวัสดี')" >สวัสดี</button>
      <button @click="getValue" >กำหนดข้อมูล</button>
      <div>ข้อมูลที่กำหนด: {{ value }}</div>
    </div>
    
  </template>
  
  <script>
  export default {
    name: 'CountBtn',
    data() {
      return {
        value: ''
      }
    },
    methods: {
      greeting(text){
        alert(text)
      },
      getValue(){
        this.value = prompt('Enter Data:')
      }
    }
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  
  </style>
  