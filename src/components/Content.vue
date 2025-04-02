<template>
  <main class="content">
    <h2>Users</h2>
    <ul>
      <li v-for="user in users" :key="user.id">
        <div class="li_row">
          {{ user.name }}
          <button @click="toggleDetails(user.id)">{{ !user.showDetails ? 'Показати деталі' : 'Приховати деталі'
            }}</button>
        </div>
        <div v-if="user.showDetails">Email: {{ user.email }}, Phone: {{ user.phone }}</div>
      </li>
    </ul>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue';
const users = ref([]);
const fetchUsers = async () => {
  const res = await fetch('https://jsonplaceholder.typicode.com/users');
  users.value = await res.json();
  users.value.forEach(user => user.showDetails = false);
};
const toggleDetails = (id) => {
  const user = users.value.find(user => user.id === id);
  if (user) user.showDetails = !user.showDetails;
};
onMounted(fetchUsers);
</script>

<style>
.content {
  flex: 1;
  padding: 30px 20px;
  min-height: calc(100vh - 100px);
  color: black;
}

ul {
  padding: 10px;
}

li {
  margin-bottom: 20px;
}

.li_row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 10px;
}
</style>