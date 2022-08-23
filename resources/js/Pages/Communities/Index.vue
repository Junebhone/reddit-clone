<script setup>
import BreezeAuthenticatedLayout from '@/Layouts/Authenticated.vue';
import { Head,Link } from '@inertiajs/inertia-vue3';

defineProps({
    communities:Object
})

</script>

<template>
    <Head title="All Communities" />

    <BreezeAuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                All Communities
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="flex justify-end mb-4">
                    <Link :href="route('communities.create')" class="px-6 py-3 bg-gray-800 text-white rounded-md hover:bg-gray-700 duration-200 transition-all ease-in-out">Add Communities</Link>
                </div>
                <div class="bg-white  mx-auto overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="overflow-hidden overflow-x-auto border border-gray-100 rounded">
                                <table class="min-w-full text-sm divide-y divide-gray-200">
                                    <thead>
                                    <tr class="bg-gray-50">
                                        <th class="px-4 py-4 font-medium text-left text-gray-900 whitespace-nowrap">Name</th>
                                        <th class="px-4 py-4 font-medium text-left text-gray-900 whitespace-nowrap">Slug</th>
                                        <th class="px-4 py-4 font-medium text-left text-gray-900 whitespace-nowrap"></th>
                                    </tr>
                                    </thead>

                                    <tbody class="divide-y divide-gray-100">
                                    <tr v-for="community in communities" :key="community">
                                        <td class="px-4 py-4 font-medium text-gray-900 whitespace-nowrap">{{ community.name }}</td>
                                        <td class="px-4 py-4 text-gray-700 whitespace-nowrap">{{ community.slug }}</td>
                                        <td class="p-4 flex justify-end gap-5 whitespace-nowrap">
                                            <Link :href="route('communities.edit',community.id)" class="text-gray-700">Edit</Link>
                                            <Link :href="route('communities.destroy',community.id)" method="delete" as="button" type="button" class="text-red-700">Delete</Link>
                                        </td>
                                        
                                         

                                    </tr>
                                    </tbody>
                                </table>
                     </div>

                </div>

            </div>
        </div>
    </BreezeAuthenticatedLayout>
</template>

