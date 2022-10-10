<template>
  <div class="quiz">
    <h1>Quizページ</h1>
    <p>Q1:何符でしょうか？（ロン）</p>
    <ul>
      <li v-for="hai in quizHais">
        <img :src="hai.image" />
      </li>
    </ul>
    <label>
      <input type="radio" :value="30" v-model="fu" />
      <span>30</span>
    </label>
    <label>
      <input type="radio" :value="40" v-model="fu" />
      <span>40</span>
    </label>
    <label>
      <input type="radio" :value="50" v-model="fu" />
      <span>50</span>
    </label>
    <label>
      <input type="radio" :value="60" v-model="fu" />
      <span>60</span>
    </label>
    <button @click="checkAnswer(fu)">回答する</button>
    <div v-if="displayAnswer">
      <div v-if="notAnswered">
        <p>選択肢から回答を選択してください</p>
      </div>
      <div v-else>
        <p v-if="correct">正解です</p>
        <p v-else>不正解です</p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { Hai } from '../types/hai';

const fu = ref(0);
const displayAnswer = ref(false);
const notAnswered = ref(true);
const correctAnswer = ref(60);
const correct = ref(false);

let quizHais: Hai[] = [
  {
    id: 1,
    number: 1,
    kind: 'manzu',
    yaochu: true,
    image: 'assets/img/manzu_all/p_ms1_1.gif',
  },
  {
    id: 1,
    number: 1,
    kind: 'manzu',
    yaochu: true,
    image: 'assets/img/manzu_all/p_ms1_1.gif',
  },
  {
    id: 1,
    number: 1,
    kind: 'manzu',
    yaochu: true,
    image: 'assets/img/manzu_all/p_ms1_1.gif',
  },
  {
    id: 2,
    number: 2,
    kind: 'manzu',
    yaochu: false,
    image: 'assets/img/manzu_all/p_ms2_1.gif',
  },
  {
    id: 2,
    number: 2,
    kind: 'manzu',
    yaochu: false,
    image: 'assets/img/manzu_all/p_ms2_1.gif',
  },
  {
    id: 2,
    number: 2,
    kind: 'manzu',
    yaochu: false,
    image: 'assets/img/manzu_all/p_ms2_1.gif',
  },
  {
    id: 21,
    number: 3,
    kind: 'sozu',
    yaochu: false,
    image: 'assets/img/sozu_all/p_ss3_1.gif',
  },
  {
    id: 21,
    number: 3,
    kind: 'sozu',
    yaochu: false,
    image: 'assets/img/sozu_all/p_ss3_1.gif',
  },
  {
    id: 21,
    number: 3,
    kind: 'sozu',
    yaochu: false,
    image: 'assets/img/sozu_all/p_ss3_1.gif',
  },
  {
    id: 22,
    number: 4,
    kind: 'sozu',
    yaochu: false,
    image: 'assets/img/sozu_all/p_ss4_1.gif',
  },
  {
    id: 22,
    number: 4,
    kind: 'sozu',
    yaochu: false,
    image: 'assets/img/sozu_all/p_ss4_1.gif',
  },
  {
    id: 22,
    number: 4,
    kind: 'sozu',
    yaochu: false,
    image: 'assets/img/sozu_all/p_ss4_1.gif',
  },
  {
    id: 33,
    character: '發',
    kind: 'sangenpai',
    yaochu: true,
    image: 'assets/img/tupai_all/p_ji_h_1.gif',
  },
  {
    id: 33,
    character: '發',
    kind: 'sangenpai',
    yaochu: true,
    image: 'assets/img/tupai_all/p_ji_h_3.gif',
  },
];

const checkAnswer = (answer: number) => {
  displayAnswer.value = true;
  if (answer === 0) return;

  notAnswered.value = false;
  if (correctAnswer.value === answer) {
    correct.value = true;
  }
};
</script>
