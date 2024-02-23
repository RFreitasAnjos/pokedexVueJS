<script setup>
import { RouterLink, RouterView } from 'vue-router'
import 'bulma/css/bulma.min.css';
import navbar from './components/navbar.vue';
import './complements/style.css';
</script>
<template>
<navbar></navbar>
  <RouterView />
</template>