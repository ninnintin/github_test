<template>
  <div>
    <h1>Stream Reports</h1>
    <ul>
      <li v-for="report in streamReports" :key="report.id">
        {{ report.title }} - {{ report.description }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const streamReports = ref([]);
// Hi i would like to change this
onMounted(async () => {
  try {
    const response = await axios.get('http://51.159.111.59:8085/api/admin/stream-reports?page=1');
    streamReports.value = response.data; // Assuming the API response is an array of objects
  } catch (error) {
    console.error('Error:', error);
  }
});
</script>
