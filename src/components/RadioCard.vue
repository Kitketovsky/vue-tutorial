<script setup>
  const props = defineProps({
    id: { type: String, required: true },
    value: { type: String, required: true },
    image: { type: String, required: true },
    label: { type: String, required: true },
    option: { type: String, required: true },
    name: { type: String, required: true },
  });

  const model = defineModel({
    type: String,
    required: true,
    default: "",
  });
</script>

<template>
  <div>
    <input type="radio" :id :value :name v-model="model" />

    <label :for="id">
      <div v-if="!!image" class="image__wrapper">
        <img :src="image" alt="" />
      </div>

      <div class="option">
        <span class="option__variant">{{ option }}</span>
        <span class="option__value">{{ label }}</span>
      </div>
    </label>
  </div>
</template>

<style scoped>
  .image__wrapper {
    aspect-ratio: 1/1;
  }

  div:has(input:checked) {
    border: 1px solid red;
  }

  label {
    gap: 1rem;
    width: fit-content;
    border: 1px solid black;
    border-radius: 5px;
    padding: 5px;
  }

  label,
  .option {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  img {
    object-fit: contain;
    width: 30px;
  }

  input {
    position: absolute;
    overflow: hidden;
    white-space: nowrap;
    margin: 0;
    padding: 0;
    height: 1px;
    width: 1px;
    clip: rect(0 0 0 0);
    clip-path: inset(100%);
  }

  div:has(input:focus) {
    border: 1px solid blue;
  }

  .option__variant {
    aspect-ratio: 1/1;
    display: block;
    width: 25px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: antiquewhite;
  }
</style>
