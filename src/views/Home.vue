<template>
  <div class="home">
    <transition name="fade">
      <Toast v-if="showToast" />
    </transition>
    <Todos @badValue="triggerToast" />
  </div>
 
</template>


<script>
import { ref } from 'vue'
import Toast from '../components/Toast'
import Todos from '../components/Todos'

export default {
  components: { Toast, Todos },
  setup() {
    const showToast = ref(false)
    const showP = ref(false)

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => showToast.value = false, 3000)
    }

    return { showToast, triggerToast ,showP}
  }
}
</script>

<style>
    /* .fade-enter-from{
      opacity: 0;
      transform: translateY(-60px);
     
    } */
    .fade-enter-active{
       animation: wobble 0.5s ease;
    }

    .fade-leave-from{
      opacity: 1;
      transform: translateY(0);
    }
    .fade-leave-to{
      opacity: 0;
      transform: translateY(-60px);
    }
    .fade-leave-active{
        transition: all 1s ease;
    }


    @keyframes wobble {
      0%{ transform: translateY(-60px);opacity: 0;}
      50%{ transform: translateY(0px);opacity: 1;}
      60%{ transform: translateX(8px);}
      70%{ transform: translateX(-8px);}
      80%{ transform: translatex(8px);}
      90%{ transform: translateX(-8px);}
      100%{transform: translateX(0);}
    }
</style>
