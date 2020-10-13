<template>
    <app-layout>
        <template #header>
            <div class="text-xl text-indigo-500 text-center">Liste des formations</div>
        </template>
        <div class="py-3" v-for="course in this.coursesList" v-bind:key="course.id">
            <div class="rounded shadow mx-8 bg-white p-4">
                <div class="text-sm text-gray-400">Mise en ligne par: <span class="text-indigo-400">{{ course.user.name }}</span>  -  <span class="text-gray-500 text-sm">{{ course.participants }} participant<span v-if="parseInt(course.participants) > 1">s</span></span></div>
                <div class="flex justify-between items-center">
                    <div class="text-4xl">{{ course.title }}</div>
                    <div class="text-sm text-gray-300">{{ course.episodes_count }} Episode<span v-if="parseInt(course.episodes_count) > 1">s</span></div>
                </div>
                <div class="text-sm text-gray-500 mt-2">{{ course.description }}</div>
                <a :href="'course/' + course.id" class="bg-indigo-700 text-white px-3 py-2 text-sm mt-3 inline-block rounded hover:bg-indigo-500">Voir la formation</a>
            </div>

        </div>
    </app-layout>
</template>

<script>

import AppLayout from './../../Layouts/AppLayout';

export default {
    components: {
        AppLayout
    },

    data() {
        return {
            coursesList: this.courses
        }
    },
  props:['courses'],

  mounted() {
      console.log(this.coursesList);
  }
}
</script>