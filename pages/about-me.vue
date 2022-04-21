<template>
  <div>
    
    <nuxt-content :document="about" style="margin:10%; margin-top:10px;" class="font-body"></nuxt-content>
  </div>
</template>

<script>
export default {
    async asyncData({$content}){
      let about = await $content('index/about-us').fetch()
      return {
          about
      }
  }, 
}
</script>
