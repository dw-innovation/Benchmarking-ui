<template>

    <Head title="Dashboard" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200">
                        <h1 class="text-3xl text-gray-800 leading-tight">Add new Script</h1>
                    </div>


                    <div class="p-12 bg-gray-300 border-b border-gray-200">
                        <form @submit.prevent="submit" class="max-w-md max-auto" >

                            <div class="input-group mb-3">
                                <label for="title" class="block mb-2 text-md text-gray-700">Please enter a title for the scripts</label>
                                <input type="text" name="title"  class="rounded focus:border-indigo-400" v-model="form.title" required>

                            </div>
                            

                            <div class="input-group mb-3">
                                <label for="fromFile" class="block mb-2 text-md  text-gray-700">Upload a Source File</label>
                                <input type="file" name="sourceFile" class="text-gray-700 rounded" @input="form.sourceFile= $event.target.files[0]">
                            </div>

                            <div clas="input-group mb-3">
                                <label for="fromFile" class="block mb-2 text-md  text-gray-700">Upload a Refrence File</label>
                                <input type="file" name="refrenceFile" class="text-gray-700 rounded" @input="form.refrenceFile= $event.target.files[0]">
                            </div>


                            <div class="mb-3 py-4">
                                <button type="submit" class="bg-gray-400 px-4 py-2 rounded">
                                    Submit
                                </button>
                            </div>

                        </form>

                    </div>
                </div>

            </div>
        </div>


    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/inertia-vue3';
import { Inertia } from '@inertiajs/inertia';
import { useForm } from '@inertiajs/inertia-vue3';
import {reactive} from 'vue';

    let form= reactive({
        title: "",
        sourceFile : "",
        refrenceFile: ""
    });

    let submit = () => {
        Inertia.post('upload', form)
    }
    
</script>
    

