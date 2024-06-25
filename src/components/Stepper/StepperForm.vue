<script setup>
  const props = defineProps({
    question: { type: String, required: true },
    description: String,
    currentStep: { type: Number, required: true },
  });
</script>

<template>
  <Transition>
    <div class="wrapper">
      <div class="header">
        <span class="question">{{ currentStep }}. {{ question }}</span>
        <span class="description" v-if="description">{{ description }}</span>
      </div>

      <slot />

      <div class="footer">
        <slot name="footer" />
      </div>
    </div>
  </Transition>
</template>

<style scoped>
  .wrapper,
  .header {
    display: flex;
    flex-direction: column;
  }

  .wrapper {
    gap: 2rem;
  }

  .header {
    gap: 0.5rem;
  }

  /* we will explain what these classes do next! */
  .v-enter-active,
  .v-leave-active {
    transition: opacity 0.5s ease;
  }

  .v-enter-from,
  .v-leave-to {
    opacity: 0;
  }
</style>
