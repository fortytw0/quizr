<template>
    <div>
        <b-jumbotron>

        <h1 id="question">
            {{currentQuestion.question}}
        </h1>
        
        <b-container>

            <b-row class="mb-2 justify-content-center">
                <b-col cols="12" class="mb-2" v-for="(option , index) in getAllOptions" :key="index">
                    <b-button variant="outline-light" class="col-6"> {{option}}</b-button>
                   
                </b-col>
            </b-row>

        </b-container>

            <b-button variant="danger" href="#">Submit</b-button>
        </b-jumbotron>
    </div>
</template>

<script>
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

    
}
</script>

<style scoped>
    #question {
        font-size: 24px;
    }

    .col-6{
        border-color: black;
        color: black;
    }
</style>