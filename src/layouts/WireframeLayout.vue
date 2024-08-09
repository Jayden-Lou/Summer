<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>

        <q-toolbar-title>
         Wireframe
        </q-toolbar-title>

       <q-btn label="Home" :to="'/'"/>
      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
defineOptions({
  name: 'MainLayout'
})
</script>
