<template>
  <div id="app">
    <b-container>
      <Header 
      :nextQuestion="nextQuestion"
      :previousQuestion="previousQuestion"
      :index="index"
      :total="questions.length"
      />
      <QuestionBox 
        :currentQuestion="questions[index]"  
      />
    </b-container>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import QuestionBox from  './components/QuestionBox.vue'

export default {
  name: 'App',
  components: {
    Header,
    QuestionBox
  },

  data() {
    return {
      questions : [],
      index : 0,
    }
  },

  mounted: function() {
    fetch('https://opentdb.com/api.php?amount=10&category=19&type=multiple' , {method: 'get'})
    .then((response) => {
    return response.json()
  }).then((jsonData) => {
    this.questions = jsonData.results
  })
  } , 

  methods: {
    nextQuestion() {
      if (this.index<9){
        this.index ++ 
      }
    },

    previousQuestion() {
      if (this.index>0) {
        this.index --
      }
    },
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
