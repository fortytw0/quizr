<template>
    <div>
        <b-jumbotron>

        <h1 id="question">
            {{currentQuestion.question}}
        </h1>
        
        <b-container>
            <b-row class="mb-2 justify-content-center">
                <b-col cols="12" class="mb-2">
                    <b-button
                      v-for="(option , index) in getAllOptions" :key="index"
                      @click="selectedOption(option , index)"
                      :variant="buttonVariant"
                      class="col-lg-5 mx-1 my-1"  
                      > {{option}}</b-button>
                                                        
                </b-col>
            </b-row>

        </b-container>

            <b-button variant="danger" href="#">Submit</b-button>
        </b-jumbotron>
    </div>
</template>

<script>
import _ from lowdash
export default {
    props:{
        currentQuestion: Object,
    },

    computed: {
        getAllOptions() {
            let allOptions = [...this.currentQuestion.incorrect_answers] 
            allOptions.push(this.currentQuestion.correct_answer)
            return allOptions
        }
    },

    methods: {
        selectedOption(option , index) {
            if (index == "3") {
                console.log( "success")
            }
            else {
                console.log("danger")
            }
            
        }
    }, 

    data() {
        return {
            correctAnswerClicked : "success",
            wrongAnswerClicked : "warning", 
            buttonVariant : "light"
        }
    }

    
}
</script>

<style scoped>
    #question {
        font-size: 24px;
    }

    .col-lg-5{
        border-color: black;
        color: black;
    }
</style>