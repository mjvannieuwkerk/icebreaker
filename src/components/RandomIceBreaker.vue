<script setup>
import { ref } from 'vue';

const iceBreaker = ref('Start');
const iceBreakers = ref([
  'What is your favorite movie or series?',
  'If you could have any superhero power, what would it be?',
  'How many languages can you speak?',
  'What makes you smile?',
  'What is your hobby?',
  'What is your favorite food?',
  'If you could only eat one meal for the rest of your life, what would it be?',
  'Where did you grow up?',
  'Do you prefer the mountain or the beach?',
  'Have you ever had a nickname?',
  'What was your favorite subject in school?',
  'Which season is your favorite?',
  'What is your favorite vacation destination?',
  'What is your favorite sport to watch?',
  'What is your favorite sport to play?',
  'What was your first job?'
]);

const getRandomIceBreaker = () => {
  const index = Math.floor(Math.random() * iceBreakers.value.length);
  iceBreaker.value = iceBreakers.value[index];
};

const sleep = async (milliseconds) => {
  return new Promise((resolve) => setTimeout(resolve, milliseconds));
};

const getRandom = async () => {
  for (let i = 0; i < 8; i++) {
    if (i % 4 === 0) {
      iceBreaker.value = '';
    } else {
      iceBreaker.value += '.';
    }
    await sleep(150);
  }
  getRandomIceBreaker();
};
</script>

<template>
  <div class="question prevent-select" @click="getRandom">
    <img v-if="iceBreaker === 'Start'" src="/icebreaker.png" />
    <span v-else>{{ iceBreaker }}</span>
  </div>
</template>

<style scoped>
.question {
  color: #38b769;
  font-size: 6rem;
  min-height: 6rem;
  text-align: center;
}
</style>
