<template>
  <div>
      <input v-model="searchTarget" @keypress.enter="reqSearch" type="text" />
  </div>
</template>

<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            searchTarget: ""
        }
    },
    methods: {
        reqSearch(){
            this.$emit("search", this.searchTarget)
        }
    }
}
</script>

<style>

</style>