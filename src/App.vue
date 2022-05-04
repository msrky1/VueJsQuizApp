<template>
  <div class="ctr">
    <questions-component
      v-if="answerQuestions < questions.length"
      :questions="questions"
      :answerQuestions="answerQuestions"
      @select-correct="selectAnswer()"
    />
    <result-component v-else :results="results" :totalCorrect="totalCorrect" />
     <button type="button" class="reset-btn" @click.prevent ="reset"
     v-if="answerQuestions === questions.length"
     
     
     >Reset</button>
  </div>
</template>

<script>
import QuestionsComponent from "./components/QuestionsComponent.vue";
import ResultComponent from "./components/ResultComponent.vue";
export default {
  name: "App",
  components: {
    ResultComponent,
    QuestionsComponent,
  },
  data() {
    return {
      answerQuestions: 0,
      totalCorrect: 0,
      questions: [
        {
          q: "What is 2 + 2?",
          answers: [
            {
              text: "4",
              is_correct: true,
            },
            {
              text: "3",
              is_correct: false,
            },
            {
              text: "Fish",
              is_correct: false,
            },
            {
              text: "5",
              is_correct: false,
            },
          ],
        },
        {
          q: 'How many letters are in the word "Banana"?',
          answers: [
            {
              text: "5",
              is_correct: false,
            },
            {
              text: "7",
              is_correct: false,
            },
            {
              text: "6",
              is_correct: true,
            },
            {
              text: "12",
              is_correct: false,
            },
          ],
        },
        {
          q: "Find the missing letter: C_ke",
          answers: [
            {
              text: "e",
              is_correct: false,
            },
            {
              text: "a",
              is_correct: true,
            },
            {
              text: "i",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Tekrar Dene!",
          desc: "Biraz daha çalış başarabilirsin!",
        },
        {
          min: 1,
          max: 1,
          title: "Başardın!",
          desc: "Çalışmak Sana çok fayda Sağladı ;)!",
        },
      ],
    };
  },
  methods: {
    selectAnswer(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }

      this.answerQuestions++;
    },
    reset() {


             this.totalCorrect = 0, 
             this.answerQuestions = 0
         
    
    }
  },
};
</script>

<style></style>
