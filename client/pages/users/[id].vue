<template>
    <div class="mx-auto max-w-5xl py-10">
        <h3 class="text-2xl">User</h3>
        <div class="py-3">
            <button @click="back()"
                class="bg-blue-800 text-white text-sm hover:bg-blue-500 order rounded-md px-4 py-1">Back</button>
        </div>
        <div v-if="user">
            <p><span class="font-bold mr-6">Name:</span> {{ user.name }}</p>
            <p><span class="font-bold mr-4">Course:</span> {{ user.course }}</p>
            <p>
                <span class="font-bold mr-2">Is Active:</span>
                <span v-if="user.is_active" class="text-green-700">✓</span>
                <span v-else class="text-red-700">X</span>
            </p>
        </div>
    </div>
</template>
  
<script setup>
import { useRoute } from "vue-router";

const route = useRoute();
const userId = route.params.id;

const { pending, data: user } = useFetch(`http://127.0.0.1:8000/api/users/${userId}`, {
    lazy: true
});

function back() {
    navigateTo(`/`);
}
</script>
