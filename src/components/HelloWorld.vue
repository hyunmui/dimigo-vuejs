<template>
  <h1>{{ msg }}</h1>
  <button @click="count++">count is: {{ count }}</button>
  <p>
    Edit <code>components/HelloWorld.vue</code> to test hot module replacement.
  </p>

  <div>
    <input type="text" v-model="keyword" />
  </div>

  <ul class="post-list">
    <li v-for="(post, index) in searchPosts" :key="index">
      <a :href="post.url">
        <h2>{{ post.title }}</h2>
      </a>
      <div class="post-info">
        <div class="post-date">{{ post.createdAt }}</div>
        <div class="post-author">
          <a href="mailto:hyunmui@outlook.kr">홍길동</a>
        </div>
      </div>
      <div class="post-summary">
        <a :href="post.url">{{ post.summary }}</a>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      keyword: "",
      count: 0,
      posts: [],
    };
  },
  mounted() {
    fetch("/list.json")
      .then((response) => response.json())
      .then((posts) => (this.posts = posts));
  },
  computed: {
    searchPosts() {
      return this.posts.filter(
        (post) =>
          this.keyword == "" ||
          post.summary.includes(this.keyword) ||
          post.title.includes(this.keyword)
      );
    },
  },
};
</script>
