<script setup>
  import StepperForm from "../StepperForm.vue";
  import RadioCard from "../../RadioCard.vue";

  import DogImage from "./../../../assets/dog.jpg";
  import CatImage from "./../../../assets/cat.jpg";
  import RabbitImage from "./../../../assets/rabbit.png";
  import RatImage from "./../../../assets/rat.jpg";

  import Button from "@/components/Button.vue";

  const value = defineModel({
    type: String,
    default: "",
    required: true,
  });

  const props = defineProps({
    nextStep: {
      type: Function,
      required: true,
    },
  });

  const CARDS = [
    { option: "A", label: "Dog", value: "dog", id: "dog", image: DogImage },
    { option: "B", label: "Cat", value: "cat", id: "cat", image: CatImage },
    {
      option: "C",
      label: "Rabbit",
      value: "rabbit",
      id: "rabbit",
      image: RabbitImage,
    },
    { option: "D", label: "Rat", value: "rat", id: "rat", image: RatImage },
  ];
</script>

<template>
  <StepperForm question="and which furry friend do you have?" :currentStep="2">
    <div class="grid">
      <RadioCard
        v-bind="card"
        v-for="card in CARDS"
        :id="card.id"
        :value="card.value"
        v-model="value"
        name="petType"
      />
    </div>

    <template #footer>
      <Button @clicked="props.nextStep" v-bind:disabled="!value">Ok</Button>
    </template>
  </StepperForm>
</template>

<style scoped>
  .grid {
    display: flex;
    justify-content: space-between;
    /* display: grid; */
    /* grid-template-columns: repeat(4, minmax(0px, 1fr)); */
    /* grid-template-rows: 1fr; */
  }
</style>
