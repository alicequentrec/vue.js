<template>
    <button class="base-button" @click="handleClick" :style="{ backgroundColor: primaryColor }" :disabled="disabled">
      <slot></slot>
    </button>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    name: 'BaseButton',
    props: {
      primaryColor: {
        type: String,
        default: '#4CAF50',
      },
      disabled: {
        type: Boolean,
        default: false,
      },
    },
    setup(props, { emit }) {
      const isDisabled = ref(props.disabled);
  
      const handleClick = () => {
        if (!isDisabled.value) {
          emit('click');
        }
      };
  
      return {
        isDisabled,
        handleClick,
      };
    },
  };
  </script>
  
  <style scoped>
  .base-button {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 10px 15px;
    font-size: 16px;
    color: #ffffff;
    border: none;
    cursor: pointer;
  }
  </style>
  