<template>
  <div>
    <h1>Posts pages</h1>
    <div class="posts-page">
      <PostList :posts="loadedPosts" :isAdmin="false" />
    </div>
  </div>
</template>

<script>
import PostList from "@/components/Posts/PostList";

export default {
  components: {
    PostList
  },
  asyncData(context, callback) {
    setTimeout(() => {
      callback(null, {
        loadedPosts: [
          {
            id: "1",
            title: "First post!",
            previewText: "preview......",
            url: "aaaa.png"
          },
          {
            id: "2",
            title: "First post!",
            previewText: "preview......",
            url: "aaaa.png"
          },
          {
            id: "3",
            title: "First post!",
            previewText: "preview......",
            url: "aaaa.png"
          }
        ]
      });
    }, 1500);
  },
  data() {
    return {
      isAdmin: {
        type: Boolean,
        default: false
      }
    };
  },
  created() {
    this.$store.dispatch("setPosts", this.loadedPosts);
  }
};
</script>

<style scoped>
.posts-page {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
