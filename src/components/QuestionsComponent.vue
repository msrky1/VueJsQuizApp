<template>
<div class="questions-ctr">
        <div class="progress">
            <div class="bar" :style="{width: `${answerQuestions / questions.length * 100}% `}"></div>
            <div class="status"> {{questions.length}} sorudan {{answerQuestions}}'ı cevaplandı</div>
        </div>
        <transition-group name="fade">
        
        
        <div class="single-question" v-for="(question, qi) in questions" :key="question.q"
         v-show="answerQuestions === qi"
        >
            <div class="question">{{question.q}}</div>
            <div class="answers" >
                <div class="answer"
                v-for="answer in question.answers" :key="answer.text"
                @click="selectAnswer(answer.is_correct)"
                >{{answer.text}}</div>
              
            </div>
        </div> 
        </transition-group>
    </div>
</template>

<script>
export default {
       props: ["questions", "answerQuestions"],
       name: "QuestionsComponent", 
       emits:['select-correct'],

       methods: {

           selectAnswer(is_correct) {


               this.$emit('select-correct' , is_correct)
           }
       },

}
</script>

<style>

</style>