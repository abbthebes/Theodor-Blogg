<template>
    <div style="margin-left:10%; margin-right:10%;">
        <!-- {{$route.params.id}} -->
        <br>
        <h1>Posts</h1>       
        <div class="flex items-center flex-wrap">
                    
            <nuxt-link to="/posts/all" v-if="$route.params.id == 'all'" class="rounded-full focus:outline-none focus:ring-2  focus:bg-indigo-50 focus:ring-indigo-800 mr-4 sm:mr-8">
                <div class="py-2 px-8 bg-indigo-200 text-indigo-700 rounded-full">
                    all
                </div>
            </nuxt-link>
            <nuxt-link to="/posts/all" v-else class="rounded-full focus:outline-none focus:ring-2 focus:bg-indigo-50 focus:ring-indigo-800 mr-4 sm:mr-8">
                <div class="py-2 px-8 text-gray-600 hover:text-indigo-700 hover:bg-indigo-100 rounded-full ">
                    all
                </div>
            </nuxt-link>

            <nuxt-link to="/posts/graph" v-if="$route.params.id == 'graph'" class="rounded-full focus:outline-none focus:ring-2  focus:bg-indigo-50 focus:ring-indigo-800 mr-4 sm:mr-8">
                <div class="py-2 px-8 bg-indigo-200 text-indigo-700 rounded-full">
                    graph
                </div>
            </nuxt-link>
            <nuxt-link to="/posts/graph" v-else class="rounded-full focus:outline-none focus:ring-2 focus:bg-indigo-50 focus:ring-indigo-800 mr-4 sm:mr-8">
                <div class="py-2 px-8 text-gray-600 hover:text-indigo-700 hover:bg-indigo-100 rounded-full ">
                    graph
                </div>
            </nuxt-link>

            <nuxt-link to="/posts/dynamic-programming" v-if="$route.params.id == 'dynamic-programming'" class="rounded-full focus:outline-none focus:ring-2  focus:bg-indigo-50 focus:ring-indigo-800 mr-4 sm:mr-8">
                <div class="py-2 px-8 bg-indigo-200 text-indigo-700 rounded-full">
                    dynamic programming
                </div>
            </nuxt-link>
            <nuxt-link to="/posts/dynamic-programming" v-else class="rounded-full focus:outline-none focus:ring-2 focus:bg-indigo-50 focus:ring-indigo-800 mr-4 sm:mr-8">
                <div class="py-2 px-8 text-gray-600 hover:text-indigo-700 hover:bg-indigo-100 rounded-full ">
                    dynamic programming
                </div>
            </nuxt-link>
            
            <nuxt-link to="/posts/data-structures" v-if="$route.params.id == 'data-structures'" class="rounded-full focus:outline-none focus:ring-2  focus:bg-indigo-50 focus:ring-indigo-800 mr-4 sm:mr-8">
                <div class="py-2 px-8 bg-indigo-200 text-indigo-700 rounded-full">
                    data structures
                </div>
            </nuxt-link>
            <nuxt-link to="/posts/data-structures" v-else class="rounded-full focus:outline-none focus:ring-2 focus:bg-indigo-50 focus:ring-indigo-800 mr-4 sm:mr-8">
                <div class="py-2 px-8 text-gray-600 hover:text-indigo-700 hover:bg-indigo-100 rounded-full ">
                    data structures
                </div>
            </nuxt-link>
        </div>
        <br>
        <div class="flex flex-wrap" style="justify-content: center; margin-bottom:200px">
          <div @click="goToDish(page.id)" class="w-56 m-6" style="cursor: pointer;" v-for="page in pages" :key="page.id">
            <PostItemComponent :item="page"></PostItemComponent>
          </div>
        </div>
        <div class="h-0 2xl:h-28"></div>
        
        <!-- <nuxt-content :document="post"></nuxt-content>
        <h1>{{ post.title }}</h1> -->
    </div>
</template>

<script>
export default {
    async asyncData({$content, params}){
        let pages = await $content('postsmd').sortBy('nr', 'desc').without(['body']).fetch()
        // sortBy('id', 'desc').limit() 
        pages = pages.filter(function (page) {
            for(let i = 0; i < page.theme.length; i++){ 
                if (page.theme[i] === params.id) return true;
            }
            return false;
        })
        return {
            pages
        }
    }, 
    methods: {
        goToDish(id) {
        this.$router.push('/blogpost/'+id)
        }
    }
}

</script>




