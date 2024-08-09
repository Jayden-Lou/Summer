<template>
  <q-dialog v-model="visible">
    <q-card class="q-dialog-plugin">
      <q-form
        class="q-gutter-md q-pa-md"
      >
        <q-input
          outlined
          v-model="data.title"
          label="Write your title *"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Please type something']"
        />

        <q-input
          outlined
          v-model="data.description"
          label="Write your description *"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Please type something']"
        />

      </q-form>
    </q-card>
  </q-dialog>
</template>

<script setup>

import {ref} from "vue";

const visible = ref(false)

function open(){
  visible.value = true
}
defineExpose({open})

defineProps({
  data:{
    type: Object
  }
})


</script>
