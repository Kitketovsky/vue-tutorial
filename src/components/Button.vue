<script setup>
  const props = defineProps({
    label: { type: String },
    type: { type: String, default: "button" },
    disabled: { type: Boolean, default: false },
  });
</script>

<template>
  <button v-on:click="$emit('clicked')" :type :disabled>
    <slot />
  </button>
</template>

<style scoped>
  button {
    background-color: rgb(0, 0, 0);
    color: white;
    border-radius: 0.5rem;
    padding: 0.5rem 1rem;
  }

  button:hover {
    cursor: pointer;
  }

  button:disabled {
    background-color: rgb(0, 0, 0, 0.6);
    cursor: not-allowed;
  }
</style>
