<template>
  <div>
    <div><img src="\pictures\code_text_programming_146694_2560x1080.jpg" class="z-0" style="height:60vh; object-fit: cover;"></div>
    
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
        <h1>New posts</h1>
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