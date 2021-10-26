<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>
      <button @click="sendRequest">click me</button>
    </p>
  </div>
</template>

<script>
export default {
  name: 'About',
  components: {
    
  },
  methods: {
    sendRequest(){
      this.axios.get('/getArticleList').then(res => {
        
      });
    }
  }
}
</script>

