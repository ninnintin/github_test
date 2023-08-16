<template>
  <div>
    <h1>Stream Report Details</h1>
    <div v-if="streamReportDetails">
      <h2>{{ streamReportDetails.title }}</h2>
      <p>{{ streamReportDetails.description }}</p>
      <!-- Display other details as needed -->
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const streamReportDetails = ref(null);

onMounted(() => {
  axios.get('http://127.0.0.1:8000/api/admin/stream-reports/2')
    .then(response => {
      streamReportDetails.value = response.data;
    })
    .catch(error => {
      console.error('Error fetching stream report details:', error);
    });
});
</script>
