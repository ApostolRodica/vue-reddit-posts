<template v-if="post">
  <div class="reddit-list-item">
    <div class="thumbnail"
      v-if="post?.data?.thumbnail && post?.data?.thumbnail_width && post?.data?.thumbnail != 'default'" 
      :style="{backgroundImage: 'url(' + post.data.thumbnail + ')'}"
    >
    </div>
    <div v-else class="thumbnail"></div>
    <div class="post-info">
      <a
        v-if="post?.data?.title"
        :href="'https://www.reddit.com' + post.data.permalink"
        target="_blank"
      >{{post.data.title}}</a>
      <p>{{post?.data?.subreddit}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "RedditListItem",
  props: ['post'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.reddit-list-item {
  display: flex;
  background-color: #fff;
  width: 100%;
  padding: 0.5rem;
}
.thumbnail {
  width: 30%;
  height: 100px;
  margin-right: 0.5rem;
  background-color: #eee;
  background-size: cover;
  background-position: center;
  background-image: url(../assets/no-image-icon.jpg);
}
.post-info {
  width: 70%;
}
.post-info a {
  color: #000;
  font-size: 1.2rem;
  text-decoration: none;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
.post-info p {
  margin: 0;
  font-size: 0.9 rem;
  font-style: italic;
  color: #42b983;
}
</style>
