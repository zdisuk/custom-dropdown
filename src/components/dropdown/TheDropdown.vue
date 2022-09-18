<template>
  <div class="wrapper">
    <div class="input-bar" @click="showOptions">
      <input
      	v-model="userInput"
      	class="input-bar__search"
      	placeholder="Click to filter"
      	type="text"
      >
      <div class="input-bar__button" @click.stop="toggleOptionsVisibility">
        <div class="input-bar__arrow"></div>
      </div>
    </div>
    <div class="list" v-if="optionsIsVisible">
      <div class="list__title">Simple filter</div>
      <div class="list__options" ref="options">
        <p
        	v-for="user in filteredList"
        	class="list__option"
          ref="option"
        	:key="user.id"
        	:class="{active: user.isActive === 'active', highlight: user.isActive === 'highlight'}"
        	@click="selectOptionByClick(user)"
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
      userInput: "",
      filteredList: [],
      counter: -1,
      selectedOptionId: null,
      times: 1,
    }
  },

  mounted(){
    this.resetFilter()

    window.addEventListener("click", (event) => {
      if (event.target.tagName === "BODY"){
        this.hideOptions()
      }
    })

    window.addEventListener("keyup", (event) => {
      if (event.key === "ArrowUp" && this.counter > 0){
        this.counter--
        this.nextOption()
        if (this.counter >= 0){
          this.times--
          this.$refs.options.scrollTop = 28.5 * (this.times - 1)
        }
      }
      if (event.key === "ArrowDown" && this.counter < this.filteredList.length-1){
        this.counter++
        this.nextOption()
        if (this.counter > 0){
          this.$refs.options.scrollTop = 28.5 * this.times
          this.times++
        }
      }
      if (event.key === "Enter"){
        this.selectOptionByEnter(this.filteredList[this.counter])
      }
    })
  },

  watch: {
    userInput(){
      // When user input empty, we display all users
      if (this.userInput === ""){
        this.filteredList = this.users
      } else {
        // If element include our user input we show this elements 
        this.filteredList = this.users.filter(el => {
          return el.name.toLowerCase().includes(this.userInput.toLowerCase())
        })
      }
    },
  },

  methods: {
    toggleOptionsVisibility(){
      this.optionsIsVisible = !this.optionsIsVisible
      this.resetHighlight()
      this.resetFilter()
      this.counter = -1
      this.times = 1
    },
    hideOptions(){
      this.optionsIsVisible = false
    },
    showOptions(){
      this.optionsIsVisible = true
      this.resetHighlight()
      this.resetFilter()
      this.counter = -1
      this.times = 1
    },
    selectOptionByClick(user){
      // when we select already selected element, we reset this element
      if (this.selectedOptionId === user.id){
        this.userInput = ""
        this.selectedOptionId = null
        user.isActive = ""
      } else {
        // when we select not selected element yet, we do this element active
        this.userInput = user.name
        this.selectedOptionId = user.id
        this.resetActive()
        user.isActive = "active"
        this.hideOptions()
      }
    },
    selectOptionByEnter(user){
      if (this.optionsIsVisible){
        if (this.selectedOptionId === user.id){
          this.userInput = ""
          this.selectedOptionId = null
          user.isActive = "highlight"
        } else {
          this.userInput = user.name
          this.selectedOptionId = user.id
          this.resetActive()
          user.isActive = 'active'
          this.hideOptions()
        }
      }else if (!this.optionsIsVisible){
        this.showOptions()
      }
    },
    nextOption(){
      this.resetHighlight()
      if (this.filteredList[this.counter].isActive !== "active"){
        this.filteredList[this.counter].isActive = "highlight"
      }
    },
    resetFilter(){
      this.filteredList = this.users
    },
    resetHighlight(){
      this.users.forEach(el => {
        if (el.isActive !== "active"){
          el.isActive = ""
        }
      })
    },
    resetActive(){
      this.users.forEach(el => {
        if (el.isActive !== "highlight"){
          el.isActive = ""
        }
      })
    }
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
      max-height: 255px;
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
.active{
  background-color: gray;
  color: white;
}
.highlight{
  background-color: darkgray;
  color: black;
}
</style>