<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>

        <q-toolbar-title>
         Jayden
        </q-toolbar-title>

       <q-btn label="Wireframe" :to="'/wireframe'" flat />
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
