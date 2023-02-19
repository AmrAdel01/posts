<template>
  <div class="postContainer" v-for="post in posts" :key="post.id">
    <div class="post">
      <div class="post-content">
        <a class="post-account" href="#">
          <img class="post-avatar" src="http://placekitten.com/200/200" />

          <span class="post-username">
            @<b>userID: {{ post.userId }}</b>
          </span>
        </a>

        <div class="post-text-container">
          <h2>{{ post.title }}</h2>
          <p>{{ post.body }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      posts: {},
    };
  },
  methods: {
    async fetchPosts() {
      await axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then((response) => {
          this.posts = response.data;
        })

        .catch((error) => {
          console.log(error);
        });
    },
  },
  mounted() {
    this.fetchPosts();
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  color: #292f33;
}

.postContainer {
  border-left: 1px solid #e1e8ed;
  border-right: 1px solid #e1e8ed;
  border-top: 1px solid #e1e8ed;
  width: 588px;
  margin: 20px auto;
  border-radius: 5px;
}

.post {
  border-bottom: 1px solid #e1e8ed;
  cursor: pointer;
  min-height: 51px;
  padding: 9px 12px;
}
.post-content {
  display: block;
  font-size: 14px;
  margin-left: 58px;
  font-size: 14px;
}
.post-account {
  color: #8899a6;
  padding: 0px;
  text-decoration: none;
  line-height: 20px;
}
.post-avatar {
  float: left;
  height: 48px;
  width: 48px;
  margin-left: -58px;
  border-radius: 5px;
}

.post-username {
  font-weight: bold;
  font-size: 14px;
  color: #b1bbc3;
  padding: 0px;
}
.post-timestamp {
  font-size: 14px;
  color: #b1bbc3;
  padding: 0px;
}
.post-text-container {
  font-size: 14px;
  color: #292f33;
  line-height: 18px;
}
</style>
