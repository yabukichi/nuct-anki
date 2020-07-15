<template>
  <div class="container">
    finish
  </div>

</template>

<script>
var quiz = {vue :[
    { question: '続く　従う', answer: 'follow' ,ok:false},
    { question: '考慮する', answer: 'consider' ,ok:false},
    { question: '増加する', answer: 'increase',ok:false },
    { question: '発達させる', answer: 'develop' ,ok:false},
    { question: '続く　続ける', answer: 'continue' ,ok:false},
    { question: '（音楽が）クラシックの', answer: 'classical' ,ok:false},
    { question: 'イスラム教の', answer: 'muslim',ok:false },
    { question: '重大な', answer: 'grave',ok:false },
    { question: '肥えた', answer: 'fertile' ,ok:false},
]};

export default {
  data: function(){
    return {
      title:"英単語帳",
      answer:quiz.vue[0].answer,
      question: quiz.vue[0].question,
      number:0,
      isActive01:false,
    };
  },
  methods:{
    miss: function(){
      this.number++
      if (quiz.vue[this.number] == null){
        console.log("misssss!!")
      }else{
        this.answer = quiz.vue[this.number].answer;
        this.question = quiz.vue[this.number].question;
        this.isActive01= false
      }
    },
    clear: function(){
      this.number++
      if (quiz.vue[this.number] == null){
        router.push({ path: 'finish' })
        console.log("clearrrr!!")
      }else{
        this.answer = quiz.vue[this.number].answer;
        this.question = quiz.vue[this.number].question;
        quiz.vue[this.number].ok = true;
        this.isActive01= false;
      }
    },
     doAction: function(){
      this.message = 'こんにちは、' + this.input + 'さん！';
    }
  },
};
</script>

<style lang="scss" scope>
li{
  list-style: none;
}

.container {
  margin: 0 auto;
  width: 1024px;
  text-align: center;
  height: 100vh;
  display: flex;
  flex-flow: column;
}

.ankicard{
  border: solid 2px #dcdcdc;
  position: relative;
  &.answer{
    opacity: 0;
    transition: 0s;
  }
  &.active{
    opacity: 1;
    transition: 0.5s;
  }
}

.number{
  position: absolute;
  top: 5px;
  left: 5px;
}

.anki-contents{
  width: 700px;
  height: auto;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 40px;
  color: #35495e;
  letter-spacing: 1px;
  .type{
    padding : 5px 10px;
    color: blue;
  }
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
