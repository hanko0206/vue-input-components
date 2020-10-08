<template>
  <div id="app">
    <h1>Reusable components</h1>
    <hr>
    <p>Minimum eight characters, at least one letter and one number</p>
    <vue-input 
      v-model="password_value"
      type="password"
      label="Enter valid password"
      placeholder="Password"
      :input_validator="checkInput"
      :required="true"
      />
      <hr>
      <h3>Checkbox and Radio button</h3>
      <p>Checkbox</p>
      <vue-radio-checkbox @click="selectedCourse( $event)" label="Vue" value="Vue"/>
      <vue-radio-checkbox @click="selectedCourse($event)" label="React" value="React"/>
      <vue-radio-checkbox @click="selectedCourse($event)" label="Angular" value="Angular"/>
      <p>Selected course(s) are: {{course.join(", ")}}</p>
      <p>Radio button</p>
      <vue-radio-checkbox type="radio" value="Male" label="Male" name="gender" @click="selectedGender($event)"/>
      <vue-radio-checkbox type="radio" value="Female" label="Female" name="gender" @click="selectedGender($event)"/>
      <vue-radio-checkbox type="radio" value="Others" label="Others" name="gender" @click="selectedGender($event)"/>
      <p>Selected gender is: {{ gender }}</p>
      <hr>
      <h3>Button</h3>
      <vue-button @click="buttonClicked" label="Button w/ click event"/> <br><br>
      <vue-button :fullWidth="true" label="Button w/ full width"/><br><br>
      <vue-button :fullWidth="true" label="Danger button full width" :isDanger="true"/><br><br>
      <vue-button :fullWidth="true" label="Success button full width" :isSuccess="true"/><br><br>
      <vue-button :fullWidth="true" label="Success button full width" :isWarning="true"/>
  </div>
</template>

<script>
import VueInput from "./components/molecules/vue-input"
import VueRadioCheckbox from "./components/molecules/vue-radio-checkbox"
import VueButton from "./components/atoms/vue-button"
export default {
  data() {
    return {
      password_value: "",
      course: [],
      gender: ""
    }
  },
  components: {
    VueInput,
    VueRadioCheckbox,
    VueButton
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
     return result; 
    },
    selectedCourse(event) {
      if(event.target.checked ) {
        this.course.push(event.target.value)
      }else {
        const index = this.course.findIndex(c => c === event.target.value)
        this.course.splice(index, 1)
      }
    },
    selectedGender(e) {
      this.gender = e.target.value
    },
    buttonClicked() {
      alert("Button was clicked")
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
