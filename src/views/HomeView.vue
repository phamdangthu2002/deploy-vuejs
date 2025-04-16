<script setup>
import { computed, onMounted, ref } from 'vue';
import { useRouter } from 'vue-router';

const users = ref([]);
const keySearch = ref('');

const router = useRouter();
onMounted(() => {
  //cach 1
  // fetch('https://jsonplaceholder.typicode.com/users')
  //     .then(response => response.json())
  //     .then(json => users.value = json);

  //cach 2
  (async () => {
    const response = await fetch('https://jsonplaceholder.typicode.com/users');
    const data = await response.json();
    users.value = data;
  })();
});

const filterUsers = computed(() => {
  return users.value.filter(user => user.name.toUpperCase().indexOf(keySearch.value.toUpperCase()) !== -1 || user.email.toUpperCase().indexOf(keySearch.value.toUpperCase()) !== -1);
});
</script>

<template>
  <main style="color: #000;padding: 2rem;">
    <input type="text" placeholder="Enter search..." v-model="keySearch" />
    <div class="group-card">
      <div v-if="filterUsers.length === 0">
        <p>Không tìm thấy kết quả</p>
      </div>
      <div class="card-item" v-for="user in filterUsers">
        <div @click="router.push({path:`/todo/${user?.id}`})"> 
          <h2>{{ user?.name }}</h2>
          <i>{{ user?.email }}</i>
        </div>
      </div>
    </div>
  </main>
</template>
<style></style>