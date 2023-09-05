<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
defineProps({
    user: {
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
        <div class="flex flex-col gap-y-2">
            <p>Kullanıcı Profili</p>

            <p>Kullanıcı Adı:{{ user.name }}</p>
            <p>Kullanıcı Emaili:{{ user.email }}</p>
        </div>
    </AuthenticatedLayout>
</template>
