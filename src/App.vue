<template>
  <div id="app">
    <h1>Reusable components</h1>
    <hr/>
    <p>Minimum eight characters, at least one letter and one number</p>
    <vue-input 
      v-model="password_value"
      type="password"
      label="Enter valid password"
      placeholder="Password"
      :input_validator="checkInput"
      :required="true"
      />
  </div>
</template>

<script>
import VueInput from "./components/atoms/vue-input.vue"
export default {
  data() {
    return {
      password_value: ""
    }
  },
  components: {
    VueInput
  },
  methods: {
    checkInput(value){
      let result = {}
      const regex = /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$/;
      if(value) { //check if input has value
        result = !regex.test(value) ? 
        {
          result: "is-error",
          message: "Invalid password!"
        }
        : { result: 'is-success', message: "Valid password"}
      }
      console.log(result)
     return result; 
    }
  }
}
</script>

<style lang="scss" scoped>
  #app {
    padding: 10%;
    p {
     font-weight: bold;
    }
  }
</style>
