<script setup>
import AFormDialog from "components/AFormDialog.vue";
import {ref} from "vue";

defineProps({
  isReversed: {
    type: Boolean,
    default: false
  },
  data:{
    type: Object
  }
})
const form = ref(null)

function showForm(){
  form.value.open()
}

</script>

<template>
  <div :class="isReversed ? 'reverse' : ''" class="row q-mt-md">
    <div class="col-xs-12 col-md-5 bg-grey-3 row justify-center items-center">
      <img :src="data.imagePath" style="max-width:100%"/>
    </div>
    <div class="col-xs-12 col-md-7 column items-center justify-center">
      <div class="row justify-center full-width relative-position">
        <h4 class="font">{{ data.title }}</h4>
        <div class="absolute-right column justify-center">
          <q-btn label="Edit" @click="showForm" />
        </div>
      </div>
      <h6 class="q-my-xs-none q-my-auto q-mx-lg">{{ data.description }}</h6>
    </div>
  </div>
  <AFormDialog :data="data" ref="form" />
</template>

<style scoped>

</style>
