<template>
    <iframe width="720" height="480"
        :src="'https://www.youtube.com/embed/'+id.videoId">
    </iframe>
</template>

<script>
export default {
    name: 'VideoPlayer',
    props: {
        id : Object
    }, 
}
</script>

<style>

</style>