<template>

<transition name="expand" @before-enter="beforeEnter" @enter="enter"  :css="false">

      <ul v-show="list.open" class="list-item">
        <li class="sub-items"
        v-for="(item,i) in list.sublist " :key="i">
        {{item}}
        </li>
      </ul>

</transition>
</template>

<script>
import { gsap } from 'gsap';




  export default {
   

    props:[
      'list'
    ],

    methods:{
      beforeEnter(el) {
      gsap.set(el, {
        x:"-200px",
        opacity:0
      })
    },
    enter(el, done) {
      gsap.to(el, {
        duration: 1,
        opacity: 1,
        x: 0,
        onComplete: done
        
      })
    },


    

     
    }
  }
</script>

<style lang="scss" scoped>
  .list-item{
    list-style:none;


    .sub-items{
      padding: 10px;
      text-indent: 20px;
      color: #fefefe;
      background-color: #835858;
      border-top:1px solid #222 ;


      &:hover{
        color: #835858;
        background-color: #fff0f0;
      }
    }
  }

  .expand-enter-active{
    transition: height .5s ease-in-out;
    overflow: hidden;
  }

</style>