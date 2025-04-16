<script setup>
import { reactive, ref } from 'vue';

const todoData = reactive({
    email: '',
    name: '',
    phone: '',
    website: '',
});

const handleCreateNewData = async ()=>{
    console.log(todoData);
}
</script>

<template>
    <main style="color: #fff; padding: 2rem;">
        <h1 style="font-weight: bold;">Create todo</h1>
        <div style="margin-top: 1rem;">
            <input type="text" placeholder="Email" v-model="todoData.email">
        </div>
        <div style="margin-top: 1rem;">
            <input type="text" placeholder="Name" v-model="todoData.name">
        </div>
        <div style="margin-top: 1rem;">
            <input type="text" placeholder="Phone" v-model="todoData.phone">
        </div>
        <div style="margin-top: 1rem;">
            <input type="text" placeholder="Website" v-model="todoData.website">
        </div>
        <div style="display: flex;" @click="handleCreateNewData">
            <div class="btn-main" style="margin-top: 1rem; border-radius: 50px;">Create New</div>
        </div>
    </main>
</template>
