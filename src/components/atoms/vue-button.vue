<template>
  <button 
    @click="$emit('click')" 
    :class="{ 
      'full-width': fullWidth, 
      'default': defaultBtn,
      'btn-danger': isDanger,
      'btn-success': isSuccess,
      'is-warning': isWarning
      }">
      {{ label }}
    </button>
</template>

<script>
  export default {
    props: {
      label: {
        type: String,
        default: "Button"
      },
      defaultBtn: {
        type: Boolean,
        default: true
      },
      fullWidth: {
        type: Boolean,
        default: false
      },
      isDanger: {
        type: Boolean,
        default: false
      },
      isSuccess: {
        type: Boolean,
        default: false
      },
      isWarning: {
        type: Boolean,
        default: false
      }
    }
  }
</script>  

<style lang="scss" scoped>
  button {
    border: 1px solid #d8c9c9;
    padding: 7px;
    border-radius: 5px;
    font-size: 14px;
    width: auto;
    &.default {
      background-color: #fff;
    }
    &.full-width {
      width: 100%;
    }
    &.btn-danger {
      background-color: #ec7474;
      color: #fff;
    }
    &.btn-success {
      background-color: #82ca82;
      color: #fff;
    }
    &.is-warning {
      background-color: #e4bc4b;
      color: #fff;
    }
  }
</style>