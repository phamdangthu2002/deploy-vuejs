<script setup>
import { onMounted, ref } from 'vue';
import { useRoute } from 'vue-router';

const router = useRoute();
const user = ref(null);
onMounted(() => {
  //cach 1
  // fetch('https://jsonplaceholder.typicode.com/users')
  //     .then(response => response.json())
  //     .then(json => users.value = json);

  //cach 2
  (async () => {
    const response = await fetch(`https://jsonplaceholder.typicode.com/users/${router.params.id}`);
    const data = await response.json();
    user.value = data;
  })();
});
</script>

<template>
  <main style="color: #fff; padding: 2rem;">
    <div class="card-item">
      <h2>{{ user?.email }}</h2>
      <h2>{{ user?.name }}</h2>
      <h2>{{ user?.phone }}</h2>
      <h2>{{ user?.username }}</h2>
      <h2>{{ user?.website }}</h2>
    </div>
  </main>
</template>
