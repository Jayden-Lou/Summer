<template>
  <q-page class="flex column">
    <FirstSection/>
    <ASection :data="sections[0]"/>
    <ASection :data="sections[1]" :isReversed="true" />
    <ASection :data="sections[2]" />
    <ATable/>
    <AVideo :data="sections[3]" :isReversed="true" />
    <AFooter/>
  </q-page>
</template>

<script setup>

import AVideo from "components/AVideo.vue";
import ASection from "components/ASection.vue";
import ATable from "components/ATable.vue";
import {ref} from "vue";
import FirstSection from "components/FirstSection.vue";
import AFooter from "components/AFooter.vue";


defineOptions({
  name: 'IndexPage'
});


const sections = ref([
  {
    title: 'The Four Seasons',
    description: 'I think the four seasons—spring, summer, autumn, and winter—are really fun! In spring, I love seeing the flowers bloom and feeling the warm sun. Summer is my favorite because I can play outside and go swimming with my friends. When autumn comes, I like to jump in the colorful leaves and eat sweet snacks. Then in winter, it snows, and I can make snowmen and drink hot cocoa. Each season is special and makes me happy!' ,
      imagePath:"seasons.png"
  },
  {
    title: 'My Family',
    description: 'I love my family! We are very close and have a lot of fun together. My mom is kind and always helps me with my homework. My dad is funny and tells great stories. I have a younger sister who loves to play games with me. Sometimes, we go to the park or watch movies as a family. We also have nice meals together, and I enjoy talking and laughing with them. My family makes me feel happy and loved!',
    imagePath:"family.png"
  },
  {
    title: 'My favorite Food',
    description: 'My favorite food is salmon! I love its tender, flaky texture and the delicious taste. Whether it’s grilled, baked, or in sushi, it always makes me happy. Sometimes, I like it with a bit of lemon or some yummy sauce. Salmon is not only tasty but also super healthy! Eating it with my family makes it even better, and I look forward to those special meals together!',
    imagePath:"salmon.png"
  },
])


</script>

<style>


</style>

