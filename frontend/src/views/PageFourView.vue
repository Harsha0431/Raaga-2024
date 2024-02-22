<script setup>
import { computed, onMounted, ref } from "vue"
import { useRouter } from "vue-router";

const router = useRouter()

const teams = [
    {
        parent:'Chiefs',
        children:[
            {
                role:'',
                members:[
                    {
                        name:'VINAY GOTTIMUKKULA',
                        image:'https://i.postimg.cc/SKBKG2j9/vinay-2000040209-RAAGA-MAIN-CHIEF.jpg',
                    }
                    
                ]
            },
        ]
    },
    {
        parent:"Associate Chiefs",
        children:[
            {
                role:'',
                members:[
                {
                        name:'SAI BHAGYASRI',
                        image:'https://i.postimg.cc/fMvwgDsV/bhagya-2000030878-VOLUNTEER-MANAGMENT.jpg',
                    },
                    {
                        name:'KVS ABHINAV',
                        image:'https://i.postimg.cc/T2qPrPxy/KVS-ABHINAV-2100031410-STAGE-MANAGEMENT.jpg',
                    },
                    {
                        name:'SP.NAGA VENKAT',
                        image:'https://i.postimg.cc/GtQhrXKP/SP-NAGA-VENKAT-2100010070-EVENT-MANAGEMENT.jpg',
                    },
                    {
                        name:'B.SANJAY',
                        image:'https://i.postimg.cc/F9WhNp7m/SANJAY-2100049100-DESIGNING.jpg',
                    },
                    {
                        name:'J.PRAKASH',
                        image:'https://i.postimg.cc/BQSnNGZm/PRAKASH-2100049068.jpg',
                    },
                    {
                        name:'NITISHA REDDY',
                        image:'https://i.postimg.cc/gGpzDrC9/IMG-20230719-WA0023.jpg',
                    },
                    {
                        name:'G.GOUTHAMI',
                        image:'https://i.postimg.cc/4JNXDq4B/IMG-20221225-WA0051.jpg',
                    },
                    {
                        name:'S.N SRAVANI',
                        image:'https://i.postimg.cc/QtcdY8Wy/SRAVANI-2100031217-SPOT-EVENTS.jpg',
                    },
                    {
                        name:'NETHRI THIRUPATI',
                        image:'https://i.postimg.cc/pXsX61pR/NETHRI-2100031663-CREATIVE-ARTS.jpg',
                    },
                    // {
                    //     name:'K.PAVANI',
                    //     image:'https://i.postimg.cc/BQSnNGZm/PRAKASH-2100049068.jpg',
                    // }
                ]
            },
        ]
    },
    {
        parent:"Website",
        children:[{
            role: '',
            members:[
                    {
                        name:'Dinesh SriSanth Adari',
                        image:'https://i.postimg.cc/SKSSxtp7/photo-2024-02-14-16-38-29.jpg',
                    },
                    {
                        name:'Harsha Vardhan Polamarsetty',
                        image:'https://i.postimg.cc/bqfCFJGM/Whats-App-Image-2024-02-11-at-19-15-52.jpg',
                    },
                    {
                        name:'Yaswanth Boina',
                        image:'https://i.postimg.cc/YMxXjCw2/IMG-1137.jpg',
                    }
                ]
            }
        ]
    }
]

const activeParent = ref('Chiefs')
const activeParentIndex = computed(() => {
    return teams.findIndex(team => team.parent === activeParent.value);
});

const activeChild = ref(teams[activeParentIndex.value].children[0].role || '')

const activeChildIndex = computed(() => {
    const activeParentIndexValue = activeParentIndex.value;
    const activeChildValue = activeChild.value;

    if (activeParentIndexValue !== -1) {
        const activeParentChildren = teams[activeParentIndexValue].children;

        // Find the index of the active child role
        const index = activeParentChildren.findIndex(child => child.role === activeChildValue);

        return index;
    }

    return -1;
});

const handleParentNavItemClick = (team) =>{
    activeParent.value = team
    activeChild.value = teams[activeParentIndex.value].children[0].role
}

const handleChildrenNavItemClick = (role) =>{
    activeChild.value = role.role
}

onMounted(()=>{
    document.title = `Team - Raaga`
})

</script>

<template>
    <div class="flex flex-col min-h-[100vh] bg-[#1a332d] justify-center py-4 ssm:pb-12 px-8">
        <button @click="router.back()" class="arrow-icon-prev fixed top-5 left-5 duration-500">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-8 h-8">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 19.5 8.25 12l7.5-7.5" />
            </svg>
        </button>
        <span class="text-center font-montserrat font-extrabold tracking-wide text-3xl sm:text-4xl relative mt-16">Team Raaga</span>
        <div class="flex flex-col gap-8 w-full justify-center relative mt-6">
            <nav aria-label="team-parent-nav" class="flex justify-center">
                <div class="border-b-2 border-gray-300 border-opacity-50 px-8 flex flex-wrap justify-center gap-8 pb-2">
                    <button :class="activeParent==team.parent ? 'text-gray-50': 'text-gray-400'" class="text-xl hover:text-gray-300 font-semibold transition-all tracking-wider" v-for="team in teams" :key="team.parent" @click="handleParentNavItemClick(team.parent)">{{ team.parent }}</button>
                </div>
            </nav>
            <nav v-if="teams[activeParentIndex].children[0].role.length>0 || false" aria-label="team-children-nav" class="flex justify-center">
                <div class="border-b-2 border-gray-300 border-opacity-50 px-8 flex flex-wrap justify-center gap-8 pb-2">
                    <button :class="activeChild==role.role?'text-gray-50':'text-gray-400'" class="text-xl hover:text-gray-300 font-semibold transition-all tracking-wider" v-for="role in teams[activeParentIndex].children" :key="role" @click="handleChildrenNavItemClick(role)">{{ role.role }}</button>
                </div>
            </nav>
        </div>

        <div class="flex relative min-[100vh] mt-12 justify-center">
            <div class="flex sm:gap-14 gap-10 flex-wrap justify-evenly">
                <div class="group rounded-2xl cursor-pointer scale-95 hover:scale-100 transition-all bg-[#1d1e2a] max-w-[250px] max-h-[350px] md:max-w-[300px] md:max-h-[400px] overflow-hidden" v-for="(member, index) in teams[activeParentIndex].children[activeChildIndex].members" :key="index">
                    <img class="group-hover:bg-opacity-20" :src="member.image" :alt="member.name"/>
                    <div class="flex rounded-r-lg group-hover:bg-[#1a332d] group-hover:translate-x-0 group-hover:transition-all group-hover:duration-700 -translate-x-10 group-hover:backdrop:blur-xl flex-col px-4 py-2 absolute opacity-0 group-hover:opacity-100 bg-transparent bottom-3 text-center">
                        <span class="text-lg text-gray-300 font-semibold font-merriweather">{{ member.name }}</span>
                        <span class="text-md text-gray-400 font-robotoslab">{{ member.designation }}</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Merriweather:wght@700&family=Oswald:wght@400;600&family=Roboto+Slab:wght@300;400;700&display=swap');
.arrow-icon-prev{
    animation: left-right 1000ms infinite;
}

@keyframes left-right {
    0% {
        transform: translateX(0);
    }
    50% {
        transform: translateX(-5px);
    }
    100% {
        transform: translateX(0);
    }
}

</style>