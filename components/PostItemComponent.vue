<template>
    <div style="margin:auto;" class="h-56 w-56">
        <img :src="item.image" alt="post image" style="color:white;">
            
        <div class="bg-gray-700 bg-opacity-60 w-56 h-10 -mt-10 absolute">   
            <h2 style="color:white; "> {{item.title}}</h2>
        </div>
        <p >{{item.description}}</p>
        <!-- <img src="../assets/pictures/DFS-BFS/grafo.jpg" alt=""> -->
    </div>
</template>

<script>
export default {
    props:['item'],
    data() {
        return {
        }
    }
}
</script>

<style>
</style>