<template>
  <div id="app">
    <BaseLayout>
      <HomePage />
      <BaseButton @click="handleButtonClick">Click Me</BaseButton>
    </BaseLayout>
  </div>
</template>

<script>
import BaseLayout from '@/components/BaseLayout.vue';
import HomePage from '@/components/HomePage.vue';
import BaseButton from '@/components/BaseButton.vue';

export default {
  components: {
    BaseLayout,
    HomePage,
    BaseButton,
  },
  methods: {
    handleButtonClick() {
    },
  },
};
</script>
