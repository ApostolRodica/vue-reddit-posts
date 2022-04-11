<template>
  <div id="app" class="container">
    <h1>Reddit Posts</h1>
    <template v-if="posts && posts.length">
      <RedditListContainer
        :posts=posts
      ></RedditListContainer>
    </template>
  </div>
</template>

<style>
.container {
  display: block;
  max-width: 1000px;
  margin: 1.5em auto;
}
</style>

<script>
import axios from "axios";
import RedditListContainer from "./components/reddit-list-container.vue";

export default {
  name: "App",
  components: {
    RedditListContainer
  },
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    getPosts() {
      axios.get(`https://www.reddit.com/new.json?sort=random&limit=25&t=year`).then((response) => {
        let data = response?.data?.data?.children
        data.forEach(element => {
          this.posts.push(element)
        })
      })
      .catch(function(err) {
          console.log(err);
       });
    },
    getMorePosts() {
      window.onscroll = () => {
        let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight + 1 >= document.documentElement.offsetHeight;
      
        if (bottomOfWindow) {
          this.getPosts()
        }
    }
    }
  },
  beforeMount() {
    this.getPosts();
  },
  mounted() {
    this.getMorePosts()
  }
};
</script>
