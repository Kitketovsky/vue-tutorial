<script setup>
  import Input from "@/components/Input.vue";
  import StepperForm from "../StepperForm.vue";
  import Button from "@/components/Button.vue";

  const value = defineModel({
    type: String,
    required: true,
  });

  const props = defineProps({
    nextStep: { type: Function, required: true },
  });
</script>

<template>
  <StepperForm question="What's their name?" :currentStep="3">
    <Input name="petName" v-model="value" />

    <template #footer>
      <Button @clicked="props.nextStep" v-bind:disabled="!value">Ok</Button>
    </template>
  </StepperForm>
</template>
