<template>
  <q-page class="flex column">
    <AVideo/>
    <ASection :data="sections[0]"/>
    <ASection :data="sections[1]" :isReversed="true" :greyAreaText="'Local Video'" />
    <ASection :data="sections[2]" />
    <ATable/>
    <ASection :data="sections[3]" :isReversed="true" :greyAreaText="'Youtube Video'" />
  </q-page>
</template>

<script setup>

import AVideo from "components/wireframe/AVideo.vue";
import ASection from "components/wireframe/ASection.vue";
import ATable from "components/wireframe/ATable.vue";
import {ref} from "vue";

defineOptions({
  name: 'IndexPage'
});


const sections = ref([
  {
    title: '1',
    description: '1',
  },
  {
    title: '2',
    description: '2',
  },
  {
    title: '',
    description: '',
  },
  {
    title: '',
    description: '',
  },
  {
    title: '',
    description: '',
  }
])


</script>

<style>


</style>

