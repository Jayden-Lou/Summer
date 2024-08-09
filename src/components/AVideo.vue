<script setup>
import AFormDialog from "components/AFormDialog.vue";
import {ref} from "vue";

defineProps({
  isReversed: {
    type: Boolean,
    default: false
  },
})
const form = ref(null)

function showForm(){
  form.value.open()
}

</script>

<template>
  <div :class="isReversed ? 'reverse' : ''" class="row q-mt-md">
    <div class="col-xs-12 col-md-5 row justify-center items-center">
      <q-video
        src="https://www.youtube.com/embed/vB-dUGMFV90?rel=0"
        style="width:100%; height: auto"
        :ratio="16/9"
      />
    </div>
    <div class="col-xs-12 col-md-7 column items-center justify-center">
      <div class="row justify-center full-width relative-position">
        <h4 class="font ">Basketball</h4>
      </div>
      <h6 class= "q-my-xs-none q-my-auto q-mx-lg">My favorite sport is basketball! I love running up and down the court, dribbling the ball, and shooting hoops. Playing with my friends is so much fun, especially when we compete in games. I enjoy practicing my skills and trying to make awesome shots. Watching basketball games on TV is exciting too! It’s a great way to stay active and have a blast with my teammates!</h6>
    </div>
  </div>
</template>

<style scoped>

</style>
