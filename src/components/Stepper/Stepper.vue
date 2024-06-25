<script setup>
  import { ref, reactive, watch } from "vue";
  import StepOwnerName from "./Steps/StepOwnerName.vue";
  import StepPetType from "./Steps/StepPetType.vue";
  import StepPetName from "./Steps/StepPetName.vue";
  import StepPetBirthday from "./Steps/StepPetBirthday.vue";
  import StepPetHealthProblems from "./Steps/StepPetHealthProblems.vue";
  import StepOwnerPhoneNumber from "./Steps/StepOwnerPhoneNumber.vue";

  const currentStep = ref(1);

  const form = reactive({
    name: "",
    phoneNumber: "",
    petType: "",
    petName: "",
    petBirthday: "",
    petProblems: "",
  });

  const MIN_STEPS = 1;
  const MAX_STEPS = 6;

  function prevStep() {
    if (currentStep.value > MIN_STEPS) {
      currentStep.value--;
    }
  }

  function nextStep() {
    if (currentStep.value < MAX_STEPS) {
      currentStep.value++;
    }
  }
</script>

<template>
  <form>
    <Transition name="slide-up" mode="out-in">
      <StepOwnerName
        v-model="form.name"
        v-if="currentStep === 1"
        v-bind:nextStep="nextStep"
      />

      <StepPetType
        v-model="form.petType"
        v-else-if="currentStep === 2"
        v-bind:nextStep="nextStep"
      />

      <StepPetName
        v-model="form.petName"
        v-else-if="currentStep === 3"
        v-bind:nextStep="nextStep"
      />

      <StepPetBirthday
        v-model="form.petBirthday"
        :petName="form.petName"
        v-else-if="currentStep === 4"
        v-bind:nextStep="nextStep"
      />

      <StepPetHealthProblems
        v-model="form.petProblems"
        v-else-if="currentStep === 5"
        v-bind:nextStep="nextStep"
      />

      <StepOwnerPhoneNumber
        v-model="form.phoneNumber"
        v-else-if="currentStep === 6"
        v:bind:onSubmit="onSubmit"
      />
    </Transition>
  </form>
</template>

<style scoped>
  .slide-up-enter-active,
  .slide-up-leave-active {
    transition: all 0.25s ease-out;
  }

  .slide-up-enter-from {
    opacity: 0;
    transform: translateY(50px);
  }

  .slide-up-leave-to {
    opacity: 0;
    transform: translateY(-50px);
  }

  form {
    position: relative;
    flex-direction: column;
    display: flex;
    row-gap: 2rem;
    align-items: center;
  }
</style>
