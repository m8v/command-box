<template>
  <div class="row">
    <form>
      <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
        <textarea
          placeholder="start typing..."
          class="cmd-box form-control"
          rows="3"
          v-model="post"
        ></textarea>
        <button class="btn-own pull-right" @click.prevent="createNew">post</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      post: ""
    };
  },
  methods: {
    createNew() {
      if (!this.post) {
        return;
      }
      this.$emit("postAdded", this.post);
      this.post = "";
    }
  }
};
</script>

<style>
.form-control {
  border-color: #009688;
}
.form-control:focus {
  border-color: #009688;
  box-shadow: none;
}

.btn-own {
  margin-top: 5px;
  padding-right: 20px;
  padding-left: 20px;
  background-color: #009688;
  border: none;
  border: 1px solid #009688;
  color: white;
}
.btn-own:focus,
.btn-own:active,
.btn-own:hover {
  outline: none !important;
  box-shadow: none;
}

.btn-own:hover {
  /* border: 1px solid #009688; */
  background: white;
  color: #009688;
}
</style>