<template>
  <div>
    <div>
      <!-- ifall jag har image-backgrounf: url så hamnar den så -->
    <!-- <div height="60vh" width="100wv" style="height:60vh; width: 100wv; background-image: url('\pictures\615b420a88a7b9f2f4813262_Web- Blog Hero (1600 x 520).png'); background-repeat: no-repeat; "> -->
      <img src="\pictures\615b420a88a7b9f2f4813262_Web- Blog Hero (1600 x 520).png" class="z-0" style="height:60vh; object-fit: cover;">  
      <div class="absolute top-24 left-16 z-10">
        <p style="font-size:50px; color: white; font-weight: bold;">Beskow Innovation</p>
        <p style="font-size:30px; color: white;">Innovation at it's finest</p>
        <div @click="$router.push('/posts/all')" class="z-10" style="cursor: pointer; padding:5px; background-color: #CB3727; font-size:12px; font-weight: medium; width: 30%;">
          <p style="color: white; margin:5px;">DISCOVER BLOGS</p> 
        </div>
      </div>
    </div>
    
    <div style="width:80vw; margin: 0% 10% 0% 10%;">
      <div class="quick-about">
        <div class="flex flex-wrap">
          <div class="w-full md:w-1/2">
            <img src="/pictures/about_blog.jpg" width="80%" style="margin:17.5%">
            <!-- <img src="https://i.redd.it/y3bg31c45kj01.jpg" width="65%" style="margin:17.5%">
            <div id="orange-thing"></div> -->
          </div>
          <div class="w-full md:w-1/2">
             <nuxt-content :document="about" style="margin:10%;" class="font-body"></nuxt-content>
          </div>
        </div>
        <h1>Latest posts</h1>
        <div class="flex flex-wrap" style="justify-content: center; margin-bottom:200px">
          <div @click="goToDish(page.id)" class="w-56 m-6" style="cursor: pointer;" v-for="page in pages" :key="page.id">
            <PostItemComponent :item="page"></PostItemComponent>
          </div>
        </div>
      </div>

      <div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({$content}){
      let about = await $content('index/short-about').fetch()
      let pages = await $content('postsmd').sortBy('nr', 'desc').without(['body']).fetch()
      // sortBy('id', 'desc').limit() 
      return {
          about, pages
      }
  }, 
  methods: {
    goToDish(id) {
      this.$router.push('/blogpost/'+id)
    }
  }
}
</script>




<style>
  .quick-about{
    width:100%;
  }
  #orange-thing{
    position: absolute; 
    width:20%; 
    height:70%; 
    background-color: #f0b541;
    top: 67.5%;
    left: 12%;
    z-index: -1;
  }
  .bloglist{
    width: 30%;
  }
</style>



// https://www.behance.net/gallery/117672893/Cooking-blog?tracking_source=search_projects%7Cblog%20design