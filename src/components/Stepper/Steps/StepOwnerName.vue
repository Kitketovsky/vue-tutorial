<script setup>
  import Input from "@/components/Input.vue";
  import StepperForm from "../StepperForm.vue";
  import Button from "./../../Button.vue";
  import { computed } from "vue";

  const model = defineModel({
    type: String,
    default: "",
    required: true,
  });

  const props = defineProps({
    nextStep: { type: Function, required: true },
  });

  const disabled = computed(() => {
    return model.value.length < 3 || model.value.length > 20;
  });
</script>

<template>
  <StepperForm question="Hello, what is your name?" :currentStep="1">
    <Input placeholder="Insert your name..." v-model="model" name="name" />

    <template #footer>
      <Button @clicked="props.nextStep" :disabled>Ok</Button>
    </template>
  </StepperForm>
</template>
