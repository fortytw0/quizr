<template>
    <div>
        <h1>Quizr</h1>
        <h4>Counter : {{index+1}}/{{total}}</h4>
        <b-nav align="center">
            <b-nav-item active> <b-button variant="outline-primary" @click="previousQuestion">Previous</b-button></b-nav-item>
            <b-nav-item><b-button variant="outline-warning">Pass</b-button></b-nav-item>
            <b-nav-item><b-button variant="outline-success" @click="nextQuestion">Next</b-button></b-nav-item>
        </b-nav>
    </div>
</template>



<script>
export default {

    props: {
        previousQuestion: Function,
        nextQuestion: Function,
        index: Number, 
        total: Number
    },
    
}
</script>