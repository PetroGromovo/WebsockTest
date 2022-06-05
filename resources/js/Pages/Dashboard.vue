<script>
import AppLayout from '@/Layouts/AppLayout.vue';
import Welcome from '@/Jetstream/Welcome.vue';

import {onMounted, ref, defineComponent} from 'vue'


export default defineComponent({

    name: 'DashboardIndex',
    components: {
        Welcome, AppLayout
    },

    setup() {

        let users = ref([
            {
                name: "John Doe",
                email: "john@example.com",
                title: "Software Engineer",
                title2: "Web dev",
                status: "Active",
                role: "Owner",
            }
        ])

        let active_todos_count = ref(0)

        function chatInit() {
            console.log('chatInit Echo::')
            console.log(Echo)

            Echo.private('home')
                .listen('NewMessage', (e) => {
                        console.log('chatInit NewMessage e::')
                        console.log(e)

                    }
                )

        }

        function DashboardIndexOnMounted() {
            console.log('DashboardIndexOnMounted::')
            chatInit()
        }

        onMounted(DashboardIndexOnMounted)


        return {
        }
    },

})


</script>

<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg">
                    <Welcome />
                </div>
            </div>
        </div>
    </AppLayout>
</template>
