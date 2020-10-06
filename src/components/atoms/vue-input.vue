<template>
  <div class="vue-input">
    <label> {{ label }} </label>
    <input 
      :type="type"
      :required="required"
      :class="inputClass"
      :placeholder="placeholder"
      :value="value"
      @input="$emit('input', $event.target.value)"
      >
      <p class="caption-text" :class="inputClass">{{ validator.message ? validator.message : caption }}</p>
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      default: "Input Label"
    },
    type: {
      type: String,
      default:""
    },
    required: {
      type: Boolean,
      default: false
    },
    value: {
      type: [String, Number],
      default:null
    },
    caption: {
      type: String,
      default: ""
    },
    input_validator: {
      type: Function,
      default: () => {
        return { result: false, message: "" };
      }
    },
    placeholder: {
      type: String,
      default: ""
    }
  },
  computed: {
    validator: function() {
      return this.input_validator(this.value)
    },
    inputClass: function() {
      return this.validator.result
    }
  }
}
</script>

<style lang="scss" scoped>
.vue-input {
 input {
    width: 100%;
    border: 1px solid #ccc;
    padding: 5px;
    &:focus {
      outline: none;
      border: 2px solid pink;
    }
    &.is-error {
      border: solid 1px red;
      &:focus {
        border: solid 2px red;
      }
    }
    &.is-success {
      border: solid 1px green;
      &:focus {
        border: solid 2px green;
      }
    }
 }
 .caption-text {
   margin: 0;
   font-style: italic;
   font-size: 12px;
   &.is-error {
     color: red;
   }
   &.is-success {
     color: green;
   }
 }
}
</style>