<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
defineProps({
    users: {
        type: Array,
    },
});
</script>


<template>
    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">Dashboard</h2>
        </template>
        Tüm Üyelerin Listesi
        <div v-for="(user, index) in users " :key="index">
            {{ index + 1 }}.
            <a :href="route('user.show', user.id)">
                Adı:{{ user.name }}</a>
            E-Mail Adresi: {{ user.email }}
        </div>
    </AuthenticatedLayout>
</template>
