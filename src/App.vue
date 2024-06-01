<template>
  <WordScreen :word = "word" :opened = "opened" />
  <MagicWheel :rotation="rotation"/>
  <div class="control">
    {{ sector }}
    <button class="button" v-if="!isRotating" @click="startWheel">Начать ход</button>
    <input class="inp" type="text">
  </div>
</template>

<script>
import WordScreen from "@/components/WordScreen.vue"
import MagicWheel from "@/components/MagicWheel.vue"

export default 
{
  data (){
    return{
      word : "Программирование",
      opened : [],
      rotation : 0,
      rotationEnd : 0,
      timer : false,
      isRotating : false,
      wheelData : ['350', '500', '450', '400', '600', '350', '500', 'm', '400', '600', '500', '200', '300', '350', '600', 'n', '500', '600', 'X2', '400', '350', '500', '600', '750', '550', '350', '500', '1000', '0', '450', '650', '400', '500', '600', 'X2', '600', '700', '400', '+', '600']
    }
  },
  name: 'App',
  components: 
  {
    WordScreen,
    MagicWheel
  },
  methods : {
    startWheel(){
      this.rotationEnd = Math.trunc(Math.random() * 40) * (360 / 40);
      console.log(this.rotationEnd);
      this.isRotating = true;
      this.timer = setInterval(() => {
          this.rotation++;
          if(this.rotation >= 360){
            this.rotation = 0;
          }
          if(this.rotation >= this.rotationEnd){
            this.isRotating = false;
            clearInterval(this.timer);
          }
      }, 25)
    }
  },
  computed : {
    sector(){
      let d = Math.trunc(this.rotation / (360 / 40));
      console.log(d);
      return this.wheelData[d];
    }
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
.button{
  width: 300px;
  height: 70px;
  background-color: #03478b;
  font-size: 30px;
  color: white;
  margin-right: 800px;
}
.inp{
  width: 300px;
  height: 60px;
  margin-left: 30px;
  margin-top: -40px;
}
</style>
