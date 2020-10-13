<template>
    <div>
        <div class="table w-full">
            <span class="table-cell align-top w-0.5"><a href="" class="rounded-full bg-gray-300 inline-block text-2xl leading-6 w-10 h-10 mx-px text-center text-white"><font-awesome-icon icon="home" class="m-auto h-10" /></a></span>
            <div class="flex h-10 mx-px">
                <div class="bg-gray-200 w-full m-auto rounded shadow table-fixed align-middle">
                    <div class="bg-green-500 text-white rounded-l text-center transition-width duration-500" :style="'width:' + percentage + '%'"><span class="text-gray-200" v-if="percentage == 0">0</span><span v-if="percentage > 0 && percentage < 100">{{ percentage }}%</span><span v-if="percentage == 100">Success</span></div>
                </div>
            </div>
            <span class="table-cell align-top w-0.5" v-if="percentage == 100"><a href="" class="rounded-full bg-green-500 inline-block text-2xl leading-6 w-10 h-10 mx-px text-center text-white"><font-awesome-icon icon="trophy" class="m-auto h-10" /></a></span><span class="table-cell align-top w-0.5" v-else><a href="" class="rounded-full bg-gray-300 inline-block text-2xl leading-6 w-10 h-10 mx-px text-center text-white"><font-awesome-icon icon="trophy" class="m-auto h-10" /></a></span>
        </div>
    </div>
</template>

<script>
export default {
    props: ['watchedEpisodes', 'episodes'],

    data() {
        return{
            watchedData: this.watchedEpisodes
        }
    },

    computed: {
        percentage() {
            let filteredEp = this.episodes.filter(courseEp => {
                return this.watchedData.find(watchedEp => {
                    return watchedEp.id === courseEp.id;
                });
            });
            return Math.ceil(filteredEp.length / this.episodes.length * 100);
        }
    },
    mounted() {
        eventBus.$on('toggleProgress', data => this.watchedData = data);
    }
}
</script>