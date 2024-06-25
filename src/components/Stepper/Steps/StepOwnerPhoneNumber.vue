<script setup>
  import Input from "@/components/Input.vue";
  import StepperForm from "../StepperForm.vue";
  import Button from "@/components/Button.vue";

  const value = defineModel({
    type: String,
    required: true,
  });

  const props = defineProps({
    onSubmit: { type: Function, required: false },
  });
</script>

<template>
  <StepperForm
    :current-step="6"
    question="And finally, what's your phone number, Vadim?"
    description="We'll give a call to to book Kitketovsky's first checkup"
  >
    <Input type="text" name="phoneNumber" v-model="value" />

    <template #footer>
      <Button @clicked="props.onSubmit" :disabled="!value">Ok</Button>
    </template>
  </StepperForm>
</template>
