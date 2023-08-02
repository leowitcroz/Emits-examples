<template>
  <div class="block" v-if="showBlock" @click="stoptimer">
    click me
  </div>
</template>


<script setup>
import { ref, defineProps, onMounted, onUpdated } from "vue"

const showBlock = ref(false);

const timer = ref();
const reactionTime = ref(0)

const props = defineProps({
    delay: Number,
})

const emit = defineEmits('update:reactionTime')

const startTimer = () =>{
  timer.value = setInterval(() => {
    reactionTime.value += 10
  }, 10);
}

const stoptimer = () =>{
  clearInterval(timer.value)
  emit('update:reactionTime', reactionTime.value)
};

onMounted(() => {
  setTimeout(() => {
    showBlock.value = true;
    startTimer();
  },
   props.delay
   );
})

</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}

</style>