<template>
  <div id="app">
    <CRMLayout :sidebarItems="data.sidebarItems" :tabs="data.tabs" :detailsData="data.detailsData"
      :personData="data.personData" />
  </div>
</template>

<script setup>
import CRMLayout from './components/CRMLayout.vue';
import { data } from '/home/vikas/gallery/src/data/crm.js'
</script>
