<template>
  <div>
    <ul v-if="articles && articles.length">
      <li v-for="article of articles">
        <p><strong>{{article.title}}</strong></p>
        <p>{{article.body}}</p>
        <p>{{article.description}}</p>
      </li>
    </ul>

    <ul v-if="errors && errors.length">
      <li v-for="error of errors">
        {{error.message}}}
      </li>
    </ul>
  </div> 
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      articles: [],
      errors: []
    }
  },

  created() {
    axios.get(`http://localhost:3000/articles`)
    .then(response => {
      this.articles = response.data
    })
    .catch(e => {
      this.errors.push(e)
    })
  }
}
</script>