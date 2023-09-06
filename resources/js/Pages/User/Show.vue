<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import Chirp from '@/Components/ChirpProfile.vue';
defineProps({
    user: {
        type: Array,
    },
    chirps: {
        type: Array,
    }
});
</script>


<template>
    <Head :title="user.name" />

    <AuthenticatedLayout>
        <div class="flex flex-col gap-y-2 max-w-7xl mx-auto p-6 lg:p-8">
            <p>Kullanıcı Profili</p>
            <p>Kullanıcı Adı:{{ user.name }}</p>
            <p>Kullanıcı Emaili:{{ user.email }}</p>
            Kullanıcının Chirpleri
            <div class="flex flex-col gap-y-2">
                <Chirp v-for="chirp in chirps" :key="chirp" :chirp="chirp" />
            </div>
        </div>
    </AuthenticatedLayout>
</template>
