<template> 
    <ul style="list-style:none;">
        <li v-for="(result, index) in results" :key="result.id.videoId"> 
            <img v-if="index!=0" :src="result.snippet.thumbnails.high.url" width="420" height="360" alt="안나오네?" />
        </li>
    </ul>
</template>

<script>
export default {
    name: 'VideoList',
    props: {
        results: Array
    }
}
</script>

<style>

</style>