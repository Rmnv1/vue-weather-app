<template>
  <div class="search">
    <span class="search__title">Enter city name</span>
    <input type="text" v-model="query" @keypress.enter="queryCreate" placeholder="Search..." class="search__field">
  </div>
</template>

<script>
export default {
  name: 'Search',
  props: {
    
  },
  data() {
    return {
      query: ''
    }
  },
  methods: {
    queryCreate() {
      this.$emit('queryCreate', {
        query: this.query
      })
    }
  }
}
</script>

<style scoped lang="scss">
.search {
  width: 100%;
  max-width: 335px;
  margin: 0 auto;
  padding-top: 6vh;
  animation: .8s fadeIn;
}
.search__title{
  display: block;
  font-size: 18px;
  color: #FFF;
  margin-bottom: 15px;
  text-align: center;
  font-weight: 600;
}
.search__field{
  width: 100%;
  border: none;
  background: rgba($color: #FFF, $alpha: .5);
  padding: 15px 15px;
  font-size: 14px;
  border-radius: 5px;
  font-family: 'Open Sans', sans-serif;
  // temp
  outline: none;
}
</style>
