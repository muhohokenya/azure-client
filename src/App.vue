<template>
  <div>
    <h1>Data from API:</h1>
    <div v-for="item in data" :key="item.id">
      {{ item }}
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  name: 'FetchData',
  setup() {
    const data = ref(null);

    let baseUrl = "https://devops-todo-api.azurewebsites.net"
    const fetchData = async () => {
      const response = await fetch(baseUrl + '/api/TodoItems');
      data.value = await response.json();
      console.log(data)
    };

    onMounted(fetchData);

    return { data };
  },
};
</script>
