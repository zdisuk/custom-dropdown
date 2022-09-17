<template>
  <div class="wrapper">
    <div class="input-bar" @click="showOptions">
      <input
        class="input-bar__search"
        placeholder="Click to filter"
        type="text"
      >
      <div class="input-bar__button">
        <div class="input-bar__arrow"></div>
      </div>
    </div>
    <div class="list" v-if="optionsIsVisible">
      <div class="list__title">Simple filter</div>
      <div class="list__options">
        <p
          v-for="user in users"
          :key="user.id"
          class="list__option"
        >{{ user.name }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    users: {
      type: Object,
      required: true
    }
  },
  
  data(){
    return {
      optionsIsVisible: false,
    }
  },

  methods: {
    hideOptions(){
      this.optionsIsVisible = false
    },
    showOptions(){
      this.optionsIsVisible = true
    },
  }

}
</script>

<style lang="scss" scoped>
.wrapper {
  width: 150px;
  min-height: 300px;
  max-height: fit-content;
}
.input-bar {
  display: flex;
  cursor: pointer;
  margin-bottom: 10px;
		&__search {
      color: #000;
      height: 40px;
      width: 80%;
      padding: 0 5px;
      text-align: center;
      font-size: 1rem;
      outline: none;
      border: 1px solid gray;
      border-right: none;
      border-radius: 4px;
      border-top-right-radius: 0;
      border-bottom-right-radius: 0;
		}

		&__button {
      width: 20%;
      height: 40px;
      border: 1px solid gray;
      display: flex;
      justify-content: center;
      align-items: center;
      border-left: none;
      border-radius: 4px;
      border-top-left-radius: 0;
      border-bottom-left-radius: 0;
		}

		&__arrow {
      border: solid black;
      border-width: 0 2px 2px 0;
      display: inline-block;
      transform: rotate(45deg);
      padding: 3px;
      transition: all 0.3s ease-out;
		}
}
.list {
  width: 150%;
  height: fit-content;
  border: 1px solid gray;
  border-radius: 4px;
		&__title {
      position: relative;
      top: 0;
      padding: 15px 10px;
      text-align: center;
      border-bottom: 1.5px solid gray;
      color: darkgray;
      font-weight: bold;
		}

		&__options {
      overflow: scroll;
      height: fit-content;
      max-height: 250px;
		}

		&__option {
      color: #333;
      padding: 5px 10px;
      display: flex;
      justify-content: center;
      font-size: 1rem;
        &:hover{
          background-color: darkgray;
          cursor: pointer;
          color: black;
        }
		}
}
</style>