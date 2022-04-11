<template v-if="posts && posts.length">
  <div class="reddit-list-container">
    <div v-for="post in posts" :key="post" class="post">
        <RedditListItem
         v-if="post?.data"
         :post=post
        >
        </RedditListItem>
    </div>
  </div>
</template>

<script>
import RedditListItem from "./reddit-list-item.vue";
export default {
  name: "RedditListContainer",
  components: {
     RedditListItem
  },
  props: ['posts'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.reddit-list-container {
  display: flex;
  flex-wrap: wrap;
  background-color: #f3f3f3;
  padding: 1em;
}
.post {
  width: 45%;
  padding: 1rem;
  display: inline-flex;
  flex-grow: 1;
}
</style>
