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
        {id: 0, name: "Alex", isActive: true,},
        {id: 1, name: "Bob", isActive: false,},
        {id: 2, name: "Jack", isActive: false,},
        {id: 3, name: "Kate", isActive: false,},
        {id: 4, name: "Joseph", isActive: false,},
        {id: 5, name: "Tom", isActive: false,},
        {id: 6, name: "Montana", isActive: false,},
        {id: 7, name: "Tony", isActive: false,},
        {id: 8, name: "Pitter", isActive: false,},
        {id: 9, name: "Caroline", isActive: false,},
        {id: 10, name: "Andrew", isActive: false,},
        {id: 11, name: "Pall", isActive: false,},
        {id: 12, name: "Brad", isActive: false,},
        {id: 13, name: "Carl", isActive: false,},
        {id: 14, name: "Luis", isActive: false,},
        {id: 15, name: "Fenix", isActive: false,},
        {id: 16, name: "Julie", isActive: false,},
        {id: 17, name: "Rihana", isActive: false,},
        {id: 18, name: "Rocky", isActive: false,},
        {id: 19, name: "Rick", isActive: false,},
        {id: 20, name: "Leonardo", isActive: false,},
        {id: 21, name: "Angelina", isActive: false,},
        {id: 22, name: "Arnold", isActive: false,},
        {id: 23, name: "Fury", isActive: false,},
        {id: 24, name: "German", isActive: false,},
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