<template>
    <div class="wheel">
        <img src="../assets/Wheel.png" alt="" :style="{ transform : `rotate(${rotation}deg)` }">
        <img src="../assets/arrow.png" alt="" class = "arrow">
    </div>
</template>

<script>
    export default{
        props : {
            rotation : Number
        }
    }
</script>

<style>
    .wheel{
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .arrow{
        width: 60px;
        margin-top: -20px;
        z-index: 100;
    }
    img{
        width: 650px;
    }
</style>