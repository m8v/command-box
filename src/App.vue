<template>
  <div class="container">
    <div class="jumbotron">
      <h1 class="display-4 text-center">helioracle command-box</h1>
      <div class="text-center">
        <i>Hint:</i> try using
        <span class="filter">#filters</span>,
        <span class="nametag">@nametags</span>, or
        <span class="deadline">/deadlines</span> in your post!
      </div>
    </div>
    <app-post-grid :posts="posts" @postDeleted="deletePost"></app-post-grid>
    <app-new-post @postAdded="newPost"></app-new-post>
  </div>
</template>

<script>
import PostGrid from "./components/PostGrid.vue";
import NewPost from "./components/NewPost.vue";

export default {
  data: function() {
    return {
      posts: []
    };
  },

  methods: {
    newPost(post) {
      const arr = post.split(" ");
      for (let i = 0; i < arr.length; i++) {
        let el = arr[i];
        if (el.length === 1) {
          return;
        } else if (el[0] === "@") {
          arr[i] = `<span class="nametag">${el}</span>`;
        } else if (el[0] === "#") {
          arr[i] = `<span class="filter">${el}</span>`;
        } else if (el[0] === "/") {
          arr[i] = `<span class="deadline">${el}</span>`;
        }
      }
      post = arr.join(" ");
      this.posts.push(post);
    },
    deletePost(index) {
      this.posts.splice(index, 1);
    }
  },

  components: {
    appPostGrid: PostGrid,
    appNewPost: NewPost
  }
};
</script>

<style>
* {
  font-family: Roboto, sans-serif;
}

span {
  font-weight: bold;
  color: #5b5b5b;
}

.nametag {
  background: #ffe599;
}
.filter {
  background: #b4a7d6;
}
.deadline {
  background: #ea9999;
}
</style>
