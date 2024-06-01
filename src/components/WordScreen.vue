<template>
    <div> 
        <h2> Игра </h2>
    </div>
    <div class="word-letters">
        <div  class="word-letter" v-for = "(letter, i) in letters" :key = "i"></div>
    </div>
</template>

<script>
    export default
    {
        props:{
            word : String,
            opened : Array
        },
        computed:{
            letters(){
                return  Array.from(this.word)
            }
        }
    }
</script>

<style>
    .word-letter
    {
        width: 65px;
        height: 115px;
        background-color: grey;
        border-radius: 10px;
    }
    .word-letters
    {
        display: flex;
        justify-content: center;
        gap: 5px;
        margin-bottom: 50px;
    }
</style>