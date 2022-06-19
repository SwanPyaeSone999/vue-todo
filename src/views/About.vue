<template>
  <div class="about">
   <transition
    appear
   name="about" 
   @before-enter="beforeEnter"
   @enter="enter"
   @after-enter="afterEnter"
   >
     <h1 >About</h1>
   </transition>
   
     <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam officia possimus delectus inventore quod quisquam culpa voluptas iusto, quae maiores quo dolorum, corporis laboriosam a dolore consequatur assumenda nam!</p>
   
  </div>
</template>

<script>
import  ref  from 'vue';
import gsap from 'gsap'
export default {
  setup() {
     
    const beforeEnter = (el) =>{
      console.log("beforeEnter -set inital state",el);
      el.style.transform  = 'translateY(-60px)';
      el.style.opaticy = 0; 
    }
    const enter = (el,done) =>{
      console.log("enter");
      gsap.to(el,{
        duration:3,
        y:0,
        opacity:1,
        ease: 'bounce.out',
        onComplete: done
      })
    }
    const afterEnter = () =>{
      console.log("afterneter")
    }
  
    return{beforeEnter,enter,afterEnter}
  }
}
</script>

<style>
  .about {
    max-width: 600px;
    margin: 20px auto;
  }

  /* .about-enter-from{
    opacity: 0;
  }
  .about-enter-active{
    transition: all 1s ease;
  } */

</style>