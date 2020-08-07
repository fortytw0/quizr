<template>
    <div>
        <h1>Quizr</h1>
        <h4>Counter : {{index+1}}/{{total}}</h4>
    </div>
</template>



<script>
export default {

    props: {
        index: Number, 
        total: Number
    },
    
}
</script>