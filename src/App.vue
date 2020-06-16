<template>
  <div id="app">
    <h1>Youtube Search</h1>
    <SearchBar @search="input" />
    <div style="float: left; display: inline-block">
      <VideoPlayer style="float: left; margin=30vw" v-if="results[0]" v-bind="results[0]" />
      <VideoList style="float: left" v-if="results" :results="results" />
    </div>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import VideoPlayer from './components/VideoPlayer.vue'
import VideoList from './components/VideoList.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoPlayer,
    VideoList,
  },
  data() {
    return {
        results: [],
    }
  },
  methods: {
        input(searchTarget) {
            // 1. 입력된 검색어를 가지고,
            const baseURL="https://www.googleapis.com/youtube/v3/search"
            const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY

            // 2. Youtube API에 요청을 보내어
            axios.get(baseURL, {
                params: {
                    key: API_KEY,
                    part: 'snippet',
                    type: 'video',
                    q: searchTarget,
                    maxResults: 10,
                }
            })
            // 3. 검색어로 검색한 결과를 가져옴
            .then(response => {
                console.log(response.data)
                this.results = response.data.items
            })
        }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
