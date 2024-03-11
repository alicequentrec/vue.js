<template>
    <div>
      <h1>Hello</h1>
      <BaseButton :primaryColor="'#2ecc71'" @click="greenButtonClick" :disabled="isButtonDisabled('green')">
        {{ greenButtonDisabled ? `En cours... (${greenButtonCountdown})` : 'Green Button' }}
      </BaseButton>
      <BaseButton :primaryColor="'#e67e22'" @click="orangeButtonClick" :disabled="isButtonDisabled('orange')">
        {{ orangeButtonDisabled ? `En cours... (${orangeButtonCountdown})` : 'Orange Button' }}
      </BaseButton>
      <BaseButton :primaryColor="'#e74c3c'" @click="redButtonClick" :disabled="isButtonDisabled('red')">
        {{ redButtonDisabled ? `En cours... (${redButtonCountdown})` : 'Red Button' }}
      </BaseButton>
    </div>
  </template>
  
  <script>
  import BaseButton from '@/components/BaseButton.vue';
  import { ref } from 'vue';
  
  export default {
    components: {
      BaseButton,
    },
    setup() {
      const greenButtonDisabled = ref(false);
      const greenButtonCountdown = ref(0);
  
      const redButtonDisabled = ref(false);
      const redButtonCountdown = ref(0);
  
      const orangeButtonDisabled = ref(false);
      const orangeButtonCountdown = ref(0);
  
      const isAnyButtonActive = ref(false);
  
      const startCountdown = (timerDuration, countdownVariable, buttonDisabledVariable) => {
        countdownVariable.value = timerDuration;
        buttonDisabledVariable.value = true;
        isAnyButtonActive.value = true;
  
        const countdownInterval = setInterval(() => {
          countdownVariable.value--;
          if (countdownVariable.value <= 0) {
            clearInterval(countdownInterval);
            buttonDisabledVariable.value = false;
  
            if (!greenButtonDisabled.value && !redButtonDisabled.value && !orangeButtonDisabled.value) {
              isAnyButtonActive.value = false;
            }
          }
        }, 1000);
      };
  
      const isButtonDisabled = (buttonColor) => {
        return isAnyButtonActive.value && buttonColor !== 'green' && buttonColor !== 'red' && buttonColor !== 'orange';
      };
  
      const greenButtonClick = () => {
        startCountdown(2, greenButtonCountdown, greenButtonDisabled);
      };
  
      const redButtonClick = () => {
        startCountdown(3, redButtonCountdown, redButtonDisabled);
      };
  
      const orangeButtonClick = () => {
        startCountdown(4, orangeButtonCountdown, orangeButtonDisabled);
      };
  
      return {
        greenButtonDisabled,
        greenButtonCountdown,
        greenButtonClick,
        redButtonDisabled,
        redButtonCountdown,
        redButtonClick,
        orangeButtonDisabled,
        orangeButtonCountdown,
        orangeButtonClick,
        isButtonDisabled,
      };
    },
  };
  </script>
  