<script setup>
  const value = defineModel({
    type: String,
    default: "",
    required: true,
  });

  const props = defineProps({
    type: { type: String, default: "text" },
    name: { type: String, required: true },
    id: String,
    placeholder: String,
  });
</script>

<template>
  <div>
    <input :type :name :id :placeholder v-bind="$attrs" v-model="value" />
  </div>
</template>

<style scoped>
  div {
    width: fit-content;
    position: relative;
  }

  div::after {
    position: absolute;
    content: "";
    bottom: -4px;
    left: 0px;
    height: 1px;
    width: 100%;
    background-color: black;
    transition: scale 0.3s ease-in-out;
    transform-origin: bottom;
  }

  input {
    border: none;
  }

  input:focus {
    outline: none;
  }

  div:has(input:focus)::after {
    scale: 1 2;
  }
</style>
