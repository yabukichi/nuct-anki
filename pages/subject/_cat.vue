<template>
  <div class="container">
    <div class="m-auto overflow-hidden">
      <h1 class="title">{{title}}<span class="type">（All）</span></h1>
      <ul>
        <li>
          <div class="my-10 px-3 py-10 m-auto rounded shadow-lg ankicard" v-on:click='isActive01=!isActive01'>
            <div class="font-bold text-xl mb-2 anki-contents">{{question}}</div>
            <div class="number question">Q.{{number+1}}</div>
          </div>
          <div class="my-10 px-3 py-10 m-auto rounded shadow-lg ankicard answer" v-bind:class='{active:isActive01}'>
            <div class="font-bold text-xl mb-2 anki-contents" >{{answer}}</div>
            <div class="number answer">A.{{number+1}}</div>
          </div>
        </li>
      </ul>
    </div>
    <div>
      正答数：{{points}}
    </div>
    <div class="flex py-10 justify-center">
      <button class="ml-5 bg-red-500 hover:bg-red-400 text-white font-bold py-2 px-4 border-b-4 border-red-700 hover:border-red-500 rounded" @click="miss">
        ×
      </button>
      <button class="ml-5 bg-green-500 hover:bg-green-400 text-white font-bold py-2 px-4 border-b-4 border-green-700 hover:green-blue-500 rounded" @click="clear">
        ○
      </button>
      
    </div>
    <router-link to="/">
      <button class="mt-10 bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
        TOP
      </button>
    </router-link>
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
      points:0,
    };
  },
  methods:{
    miss: function(){
      this.number++;
      if (quiz.vue[this.number] == null){
        this.$router.push({ path: 'finish' })
        console.log("misssss!!");
      }else{
        this.answer = quiz.vue[this.number].answer;
        this.question = quiz.vue[this.number].question;
        this.isActive01= false;
      }
    },
    clear: function(){
      this.number++;
      if (quiz.vue[this.number] == null){
        this.$router.push({ path: 'finish' })
        console.log("clearrrr!!");
      }else{
        this.answer = quiz.vue[this.number].answer;
        this.question = quiz.vue[this.number].question;
        this.isActive01= false;
        quiz.vue[this.number].ok = true;
        this.points++;
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
