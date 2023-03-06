<template>
    <div class="container">
      <div>
        <input @keyup.enter="$emit('onSearch')" class="search" type="text" v-model="store.search" placeholder="Filtra per nome">
      </div>      
    </div>
  </template>
  
  <script>
    import store from '../store'
    export default {
      data() {
        return {
          // search: '',
          store,
        }
      }
      
    }
  </script>
  
  <style lang="scss" scoped>
  .container  {
    margin: 24px 0;
    display: flex;
    align-items: center;
    gap: 24px;
  }
  input {
    border: 1px solid gray;
    height: 35px;    
    border-radius: 10px;
    padding: 0 20px;
    font-size: 18px;
  }
  </style>