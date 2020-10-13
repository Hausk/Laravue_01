<template>
    <div>
        <div class="bg-gray-400 h-screen">
            
            <div class="bg-gray-700 w-2/12 h-full">
                <div class="w-full h-3/12 m-auto">
                    <img class="h-16 w-16 rounded-full object-cover m-auto" v-if="$page.user" :src="$page.user.profile_photo_url" :alt="$page.user.name" />
                    <h1 class="text-white text-xl text-center">{{ $page.user.name }}</h1>
                    <h4 class="text-blue-400 text-sm text-center">Connecté</h4>
                </div>
                <div class="flex flex-col w-full h-4/6">
                    <a class="bg-gray-700 border-t-2 border-gray-900 h-1/5 flex object-center hover:bg-blue-400 cursor-pointer">
                        <div class="logo m-auto mx-6 ml-9 text-xl text-white">0</div>
                        <h1 class="text-white m-auto mx-6 text-xl">Dashboard</h1>
                    </a>
                    <a class="bg-gray-700 border-t-2 border-gray-900 h-1/5 flex object-center hover:bg-blue-400 cursor-pointer">
                        <div class="logo m-auto mx-6 ml-9 text-xl text-white">0</div>
                        <h1 class="text-white m-auto mx-6 text-xl">Chart</h1>
                        </a>
                    <a class="bg-gray-700 border-t-2 border-gray-900 h-1/5 flex object-center hover:bg-blue-400 cursor-pointer">
                        <div class="logo m-auto mx-6 ml-9 text-xl text-white">0</div>
                        <h1 class="text-white m-auto mx-6 text-xl">Chat</h1>
                        </a>
                    <a class="bg-gray-700 border-t-2 border-gray-900 h-1/5 flex object-center hover:bg-blue-400 cursor-pointer">
                        <div class="logo m-auto mx-6 ml-9 text-xl text-white">0</div>
                        <h1 class="text-white m-auto mx-6 text-xl">Message</h1>
                        </a>
                    <a class="bg-gray-700 border-t-2 border-b-2 border-gray-900 h-1/5 flex object-center hover:bg-blue-400 cursor-pointer">
                        <div class="logo m-auto mx-6 ml-9 text-xl text-white">0</div>
                        <h1 class="text-white m-auto mx-6 text-xl">Settings</h1>
                        </a>
                </div>

            </div>

        </div>
    </div>
</template>

<script>
    import JetApplicationLogo from './../Jetstream/ApplicationLogo'

    export default {
        components: {
            JetApplicationLogo,
        },
    }
</script>
