<template>
    <app-layout>
        <!--  Header  -->
            <div class="bg-indigo-400 w-full h-40">
                <div class="m-auto h-full w-full text-center flex flex-col">

                    <a class="text-3xl text-white h-5/12 p-15 cursor-pointer font-extrabold">{{ course.episodes[this.currentKey].title }}</a>
                    
                    <div class="time text-white flex justify-around my-2">
                        <div class="flex object-center">
                            <div><font-awesome-icon icon="clock" class="mx-1" /><span class="mx-1">20 heures</span></div>
                            <div class="ml-5"><font-awesome-icon icon="signal" class="mx-1" /><span class="mx-1">Facile</span></div>
                        </div>
                        <div>
                            <span class="mx-3">Licence</span><span class="mx-3">0</span><span class="mx-3">0</span><span class="mx-3">0</span>
                        </div>
                    </div>

                </div>
            </div>
        <!-- Header end -->

        <div class="mx-auto my-5 w-3/4">
            <div class="text-right text-gray-800 text-sm">Mis à jour le {{ course.episodes[this.currentKey].updated_at}}</div>

            <div class="py-6">
                <progress-bar :watched-episodes="watched" :episodes="course.episodes"/>
            </div>

            <div class="flex justify-between w-full mt-4" >
                <div class="w-3/4 h-96 bg-black mt-6"></div>
                <div class="w-1/5 h-2/4 py-5 bg-gray-200 shadow-lg rounded flex flex-col text-center">
                    <a href="" class="m-auto text-center px-2 py-2 shadow-outline text-indigo-400 rounded">Acceder au forum</a>
                    <p class="text-center text-2xl my-3 font-extrabold">Créé par</p>
                    <img class="w-20 h-20 text-center rounded-full m-auto mt-4 my-3" :src="$page.user.profile_photo_url" />
                    <p class="my-3">{{ $page.user.name }}</p>
                </div>

            </div>
            <div class="text-gray-500 my-7 font-semibold">{{ course.episodes[this.currentKey].description }}</div>
            
            
            <div class="mt-6">
                <ul v-for="(episode, index) in this.course.episodes" v-bind:key="episode.id">
                    <li class="mt-3 flex justify-between items-center">
                        <div>
                            Épisode n°{{ index +1 }} : {{ episode.title }}
                            <button class="text-gray-400 focus:text-indigo-400 focus:outline-none" @click="switchEpisode(index)">Voir l'épisode</button>
                        </div>    
                        <progress-button :episode-id="episode.id" :watched-episodes="watched" />
                    </li>
                </ul>
            </div>
        </div>
    </app-layout>
</template>

<script>

import AppLayout from './../../Layouts/AppLayout';
import ProgressButton from './ProgressButton';
import ProgressBar from './ProgressBar';

export default {

    components: {
        AppLayout,
        ProgressButton,
        ProgressBar
    },
  methods: {
      switchEpisode(index) {
          this.currentKey = index;

          window.scrollTo({
              top: 0,
              left: 0,
              behavior: 'smooth'
          })
      }
  },

        props:['course', 'watched', 'courses'],
    data() {
        return {
            coursesShow: this.courses,
            currentKey: 0
        }
    },

  mounted() {
      console.log(this.coursesShow);
  }
}
</script>