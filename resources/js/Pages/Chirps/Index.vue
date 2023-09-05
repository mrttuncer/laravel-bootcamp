<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import InputError from '@/Components/InputError.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import { useForm, Head } from '@inertiajs/vue3';
import Chirp from '@/Components/Chirp.vue';

const form = useForm({
    message: '',
});
defineProps(['chirps']);
</script>
 
<template>
    <Head title="Chirps" />

    <AuthenticatedLayout>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">
            <a :href="route('chirps.create')" class="rounded-xl border border-black px-8 py-3">Yeni Chirp Oluştur</a>
        </div>
        <div class="max-w-2xl mx-auto p-4 sm:p-6 lg:p-8">
            <div class="text-red-500 ">
                Total Chirps: {{ chirps.total }}
            </div>
            <div class="mt-6 bg-white shadow-sm rounded-lg divide-y">

                <Chirp v-for="chirp in chirps.data" :key="chirp.id" :chirp="chirp" />

            </div>
            <div class="flex flex-row items-center mt-4">
                <div v-for="(link, index) in   chirps.links  " :key="index" :chirp="chirp" class="">
                    <a :href="link.url" class="p-2 border border-black"
                        :class="link.active ? 'bg-red-500 text-white' : link.url == null ? 'opacity-40' : ''">{{ index
                            === 0 ? 'Önceki' :
                            index == chirps.links.length - 1 ? 'Sonraki' : link.label
                        }}</a>

                </div>
            </div>
            <p class="mt-4">
                Sayfa başına {{ chirps.per_page }} chirp görüntülenmektedir.
            </p>
        </div>
    </AuthenticatedLayout>
</template>