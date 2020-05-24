
<template>
  <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3">
    <div class="panel panel-default">
      <div class="panel-body post">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      date: ""
    };
  },
  props: ["posts"]
};
</script>

<style>
.panel {
  color: #6e6e6e;
  cursor: pointer;
  border: none;
}

.post:hover {
  background-color: #ffe2e2;
}
</style>