<script setup>
  import StepperForm from "../StepperForm.vue";
  import Button from "@/components/Button.vue";
  import Input from "@/components/Input.vue";
  import { maskitoDateOptionsGenerator } from "@maskito/kit";

  const value = defineModel({
    type: String,
    required: true,
  });

  const props = defineProps({
    petName: { type: String, required: true },
    nextStep: { type: Function, required: true },
  });

  const options = maskitoDateOptionsGenerator({
    mode: "dd/mm/yyyy",
    min: new Date(2000, 0, 1),
    max: new Date(),
  });

  const vMaskito = {};
</script>

<template>
  <StepperForm
    :question="`Cute name! How old is ${petName}?`"
    :current-step="4"
  >
    <Input name="petBirthday" v-model="value" v-maskito="options" />

    <template #footer>
      <Button @clicked="nextStep" :disabled="!value">Ok</Button>
    </template>
  </StepperForm>
</template>
