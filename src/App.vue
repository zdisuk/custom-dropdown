<template>
  <the-dropdown :users="users"></the-dropdown>
</template>

<script>
import TheDropdown from './components/dropdown/TheDropdown.vue'
export default {
  components: {
    TheDropdown
  },
  data(){
    return {
      users: [
        {id: 0, name: "Alex", isActive: "highlight",},
        {id: 1, name: "Bob", isActive: "",},
        {id: 2, name: "Jack", isActive: "",},
        {id: 3, name: "Kate", isActive: "",},
        {id: 4, name: "Joseph", isActive: "",},
        {id: 5, name: "Tom", isActive: "",},
        {id: 6, name: "Montana", isActive: "",},
        {id: 7, name: "Tony", isActive: "",},
        {id: 8, name: "Pitter", isActive: "",},
        {id: 9, name: "Caroline", isActive: "",},
        {id: 10, name: "Andrew", isActive: "",},
        {id: 11, name: "Pall", isActive: "",},
        {id: 12, name: "Brad", isActive: "",},
        {id: 13, name: "Carl", isActive: "",},
        {id: 14, name: "Luis", isActive: "",},
        {id: 15, name: "Fenix", isActive: "",},
        {id: 16, name: "Julie", isActive: "",},
        {id: 17, name: "Rihana", isActive: "",},
        {id: 18, name: "Rocky", isActive: "",},
        {id: 19, name: "Rick", isActive: "",},
        {id: 20, name: "Leonardo", isActive: "",},
        {id: 21, name: "Angelina", isActive: "",},
        {id: 22, name: "Arnold", isActive: "",},
        {id: 23, name: "Fury", isActive: "",},
        {id: 24, name: "German", isActive: "",},
      ]
    }
  }

}
</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  font-family: sans-serif;
  font-style: normal;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>