<script setup>
  import Input from "./Input.vue";

  const value = defineModel({
    type: Date,
    required: true,

    set(value) {
      return value;
    },
  });
</script>

<template>
  <!-- Day -->

  <!-- <Input name="petBirthday" :value="new Date(value).getMonth()" /> -->

  <!-- Year -->
  <!-- <Input name="petBirthday" :value="new Date(value).getFullYear()" /> -->
</template>
