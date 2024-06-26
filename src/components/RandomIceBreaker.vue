<script setup>
import { ref } from 'vue';

const iceBreaker = ref('Start');
// List of 200 questions: https://museumhack.com/list-icebreakers-questions/
const iceBreakers = ref([
  'If you could invite a celebrity over for dinner, who would it be and why?',
  'If you could have any superhero power, what would it be?',
  'If you could only eat one meal for the rest of your life, what would it be?',
  'Do you prefer the mountain or the beach?',
  'Have you ever had a nickname?',
  'Which season is your favorite?',
  'If you had to delete all but 3 apps from your smartphone, which ones would you keep?',
  'What sport would you compete in if you were in the Olympics?',
  'Teleportation or flying?',
  'Are you a morning person or a night person?',
  'If you could bring back any fashion trend what would it be?',
  'If you could write a book, what genre would you write it in?',
  'You have your own late night talk show, who do you invite as your first guest?',
  'What fictional world or place would you like to visit?',
  'If you could live in any country, where would you live?',
  'If you could be guaranteed one thing in life (besides money), what would it be?',
  'Would you rather be an Olympic gold medallist or an astronaut?',
  'What song or album could you listen to on repeat?',
  'If I visited your hometown, what local spots would you suggest I see?',
  'Would you rather explore outer space or the bottom of the ocean?'
  // 'What is your favorite movie or series?',
  // 'How many languages can you speak?',
  // 'What makes you smile?',
  // 'What is your hobby?',
  // 'What is your favorite food?',
  // 'Where did you grow up?',
  // 'What was your favorite subject in school?',
  // 'What is your favorite vacation destination?',
  // 'What is your favorite sport to watch?',
  // 'What is your favorite sport to play?',
  // 'What was your first job?'
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
  color: #2caeff;
  font-size: 6rem;
  min-height: 6rem;
  text-align: center;
  transform: translateY(-50px)
}
</style>
