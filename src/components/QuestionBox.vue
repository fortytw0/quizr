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
                      class="col-lg-5 mx-1 my-1"
                      :class="{'btn btn-success' : optionIsCorrect(option , index),  
                               'btn btn-danger':selectedOptionIsNotCorrect(option , index)}"
                      @click="selectedAnswerPosition=index"
                      > {{option}}</b-button>
                                                        
                </b-col>
            </b-row>
            <b-row>
                <b-col class="col-6" align="left">
                    <b-nav-item active> <b-button variant="outline-primary" @click="previousQuestion">Previous</b-button></b-nav-item>
                </b-col>
                <b-col align="right">
                    <b-nav-item><b-button variant="outline-success" @click="nextQuestion">Next</b-button></b-nav-item>
                </b-col>
            </b-row>

        </b-container>
        </b-jumbotron>
    </div>
</template>

<script>

import _ from 'lodash';
import '../assets/bootstrap4-neon-glow.min.css'
export default {
    props:{
        previousQuestion : Function,
        currentQuestion: Object,
        nextQuestion : Function, 
        index : Number,
        total : Number

    },

    data() {
        return {
            isCorrectAnswerClicked : null,
            selectedAnswerPosition : null,
            correctAnswerPosition : 3
        }
    },

    computed: {
        getAllOptions() {
            let allOptions = [...this.currentQuestion.incorrect_answers] 
            allOptions.push(this.currentQuestion.correct_answer)
            let shuffledOptions = _.shuffle(allOptions)
            this.resetData()
            return shuffledOptions
        }
    },
    

    methods: {
        optionIsCorrect(option , index) {
            console.log(index)
            if (this.selectedAnswerPosition !== null) {
                if (this.currentQuestion.correct_answer === option) {
                    return true
                }
            }   
            else {
                return false
            }    
        },

        selectedOptionIsNotCorrect(option , index) {
            if (this.selectedAnswerPosition === index) {
                if (this.currentQuestion.correct_answer !== option) {
                    return true
                }
            }
            else {
                return false
            }
        },

        resetData() {
            this.isCorrectAnswerClicked = null;
            this.selectedAnswerPosition = null;
            this.correctAnswerPosition = 3;
        }
    }, 
}
</script>

<style scoped>
    #question {
        font-size: 24px;
        font-family:monospace;
        color:lightgreen
    }
</style>