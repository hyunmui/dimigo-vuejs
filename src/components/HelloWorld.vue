<template>
  <h1>{{ msg }}</h1>
  <button @click="count++">count is: {{ count }}</button>
  <p>
    Edit <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>

  <PostList></PostList>
</template>

<script>
import PostList from "./PostList.vue";

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  components: {
    PostList,
  },
  data() {
    return {
      count: 0,
    };
  },
};
</script>
