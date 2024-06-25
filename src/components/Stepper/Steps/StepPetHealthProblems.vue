<script setup>
  import Input from "@/components/Input.vue";
  import StepperForm from "../StepperForm.vue";
  import Button from "@/components/Button.vue";

  const value = defineModel();

  const props = defineProps({
    nextStep: { type: Function, required: true },
  });
</script>

<template>
  <StepperForm
    :current-step="5"
    question="Do they have any pre-existing health problems you're aware of?"
  >
    <Input name="petProblems" v-model="value" />

    <template #footer>
      <Button @clicked="props.nextStep" :disabled="false">Ok</Button>
    </template>
  </StepperForm>
</template>
