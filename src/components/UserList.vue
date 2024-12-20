<template>
  <div>
    <h1>Seznam uživatelů</h1>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.name }} ({{ user.email }})
      </li>
    </ul>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  setup() {
    const users = ref([]);

    onMounted(async () => {
      const response = await fetch('http://localhost:8000/api');
      users.value = await response.json();
    });

    return { users };
  },
};
</script>

<style scoped>
h1 {
  font-family: Arial, sans-serif;
  color: #333;
}
</style>
