<template lang="pug">
  #app
    div(id="pockerArea")
      div(id="pockerArea_firstColumn")
        div(v-for="(pockerArr,index) in firstPockerArr", :key="pockerArr.name",class='pocker', :class='`pocker-${pockerArr.color}-${pockerArr.number}`', :style="index === 0 ? `top: ${index}px`:`top: ${-105*index}px`")
      div(id="pockerArea_secondColumn")
        div(v-for="(pockerArr,index) in secondPockerArr", :key="pockerArr.name",class='pocker', :class='`pocker-${pockerArr.color}-${pockerArr.number}`', :style="index === 0 ? `top: ${index}px`:`top: ${-105*index}px`")
      div(id="pockerArea_thirdColumn")
        div(v-for="(pockerArr,index) in thirdPockerArr", :key="pockerArr.name",class='pocker', :class='`pocker-${pockerArr.color}-${pockerArr.number}`', :style="index === 0 ? `top: ${index}px`:`top: ${-105*index}px`")
      div(id="pockerArea_forthColumn")
         div(v-for="(pockerArr,index) in forthPockerArr", :key="pockerArr.name",class='pocker', :class='`pocker-${pockerArr.color}-${pockerArr.number}`', :style="index === 0 ? `top: ${index}px`:`top: ${-105*index}px`")
      div(id="pockerArea_fifthColumn")
        div(v-for="(pockerArr,index) in fifthPockerArr", :key="pockerArr.name",class='pocker', :class='`pocker-${pockerArr.color}-${pockerArr.number}`', :style="index === 0 ? `top: ${index}px`:`top: ${-105*index}px`")
      div(id="pockerArea_sixthColumn")
        div(v-for="(pockerArr,index) in sixthPockerArr", :key="pockerArr.name",class='pocker', :class='`pocker-${pockerArr.color}-${pockerArr.number}`', :style="index === 0 ? `top: ${index}px`:`top: ${-105*index}px`")
      div(id="pockerArea_seventhColumn")
         div(v-for="(pockerArr,index) in seventhPockerArr", :key="pockerArr.name",class='pocker', :class='`pocker-${pockerArr.color}-${pockerArr.number}`', :style="index === 0 ? `top: ${index}px`:`top: ${-105*index}px`")
      div(id="pockerArea_eighthColumn")
        div(v-for="(pockerArr,index) in eighthPockerArr", :key="pockerArr.name",class='pocker', :class='`pocker-${pockerArr.color}-${pockerArr.number}`', :style="index === 0 ? `top: ${index}px`:`top: ${-105*index}px`")


    button(@click="shufflePocker") Shuffle
      
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      pockerArr: [],
      isShuffle: false,
    };
  },
  created() {
    for (let i = 1; i <= 52; i++) {
      let pockerColor = Math.floor(i / 13);
      if (pockerColor === 0 || (pockerColor === 1 && i % 13 === 0)) {
        this.pockerArr.push({
          name: `spade-${i}`,
          color: "spade",
          number: i
        });
      } else if (pockerColor === 1 || (pockerColor === 2 && i % 13 === 0)) {
        let pockerNum = i - 13;
        this.pockerArr.push({
          name: `heart-${pockerNum}`,
          color: "heart",
          number: pockerNum
        });
      } else if (pockerColor === 2 || (pockerColor === 3 && i % 13 === 0)) {
        let pockerNum = i - 13 * 2;
        this.pockerArr.push({
          name: `diamond-${pockerNum}`,
          color: "diamond",
          number: pockerNum
        });
      } else if (pockerColor === 3 || (pockerColor === 4 && i % 13 === 0)) {
        let pockerNum = i - 13 * 3;
        this.pockerArr.push({
          name: `club-${pockerNum}`,
          color: "club",
          number: pockerNum
        });
      }
    }
  },
  computed:{
    shufflePockerArr(){
      this.isShuffle
      let storage = ''
      for(let x=0, maxLength = this.pockerArr.length; x <maxLength;x++){
          let shuffleNum = Math.ceil(Math.random()*51)
          for(let y=0, maxLength = this.pockerArr.length; y <maxLength;y++){
            storage = this.pockerArr[shuffleNum]
            this.pockerArr[shuffleNum] = this.pockerArr[y]
            this.pockerArr[y] = storage
          }
      }
      return this.pockerArr
    },
    firstPockerArr(){
      return this.shufflePockerArr.filter((pocker,index)=>{
        if(index <7){
          return pocker
        }
      })
    },
    secondPockerArr(){
      return this.shufflePockerArr.filter((pocker,index)=>{
        if(index>=7 && index<14){
          return pocker
        }
      })
    },
    thirdPockerArr(){
      return this.shufflePockerArr.filter((pocker,index)=>{
        if(index>=14 && index<21){
          return pocker
        }
      })
    },
    forthPockerArr(){
      return this.shufflePockerArr.filter((pocker,index)=>{
        if(index>=21 && index<28){
          return pocker
        }
      })
    },
    fifthPockerArr(){
      return this.shufflePockerArr.filter((pocker,index)=>{
        if(index>=28 && index<34){
          return pocker
        }
      })
    },
    sixthPockerArr(){
      return this.shufflePockerArr.filter((pocker,index)=>{
        if(index>=34 && index<40){
          return pocker
        }
      })
    },
    seventhPockerArr(){
      return this.shufflePockerArr.filter((pocker,index)=>{
        if(index>=40 && index<46){
          return pocker
        }
      })
    },
    eighthPockerArr(){
      return this.shufflePockerArr.filter((pocker,index)=>{
        if(index>=46 && index<52){
          return pocker
        }
      })
    }
  },
  methods:{
    shufflePocker(){
      this.isShuffle = !this.isShuffle
    }
  }
};
</script>


<style lang="scss" scoped src="./assets/styles/style.scss"></style>
<style lang="scss">
body {
  background-color: steelblue;
}
#pockerArea {
  display: flex;
  .removeUp{
    position: relative;
    top: -20px;
  }
}
</style>
