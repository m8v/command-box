<template>
  <div class="row">
    <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3">
      <label>activity feed (demo)</label>
    </div>
    <app-post v-for="(post, index) in posts" :key="post" @click.native="deletePost(index)">
      <p v-html="post">{{ post }}</p>
      <!-- <p class="pull-right">date: {{ date }}</p> -->
    </app-post>
  </div>
</template>

<script>
import Post from "./Post.vue";

export default {
  computed: {
    date: function() {
      const now = new Date();
      return now;
    }
  },
  data() {
    return {
      // date: new Date()
    };
  },

  props: ["posts"],
  components: {
    appPost: Post
  },
  methods: {
    deletePost(index) {
      this.$emit("postDeleted", index);
    }
  }
};
</script>

<style scoped>
label {
  color: #009688;
}

.container {
  border: 2px solid fuchsia;
}
</style>