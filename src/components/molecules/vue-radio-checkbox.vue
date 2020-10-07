<template>
  <label>
    <input
      :type="type"
      :id="id"
      :value="value"
      :name="name"
      :checked="checked"
      @click="$emit('click',  $event)"
    />
    {{ label }}
  </label>
</template>

<script>
export default {
  props:{
    type: {
      type: String,
      default: "checkbox"
    },
    id: {
      type: String,
      default: ""
    },
    value: {
      type: String,
      default: ""
    },
    name: {
      type: String,
      default: ""
    },
    checked: {
      type: Boolean,
      default: false
    },
    label: {
      type: String,
      default: ""
    }
  }
}
</script>