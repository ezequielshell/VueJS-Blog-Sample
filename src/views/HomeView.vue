<template>
  <div class="home">
    <div class="titleBlog">
      <h1>Blog of Ezequiel</h1>
      <p>
        Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fuga, sit!
      </p>
    </div>
    <div class="content">
      <div class="addPost">
        <AddPostModal :posts="posts" />
      </div>

      <div class="posts">
        <div class="post" v-for="post in posts">
          <div class="editing">
            <div v-show="post.isEditing">
              <EditPost :post="post" />
              <button class="saveButton" @click="closeEditPost(post)">
                Save
              </button>
            </div>
            <div class="postCointainer" v-show="!post.isEditing">
              <div>
                <h1>{{ post.title }}</h1>
              </div>
              <div class="bodyPost">
                <p>{{ post.body }}</p>
              </div>
              <button
                v-if="!post.isEditing"
                class="editingButton"
                @click="editPost(post)"
              >
                {{ editPostButton }}
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

import AddPostModal from "../components/AddPostModal.vue";
import EditPost from "@/components/EditPost.vue";

export default {
  name: "HomeView",
  components: { AddPostModal, EditPost },

  setup() {
    const posts = ref([]);
    let editPostButton = ref("Edit");

    const editPost = (post) => {
      post.isEditing = true;
    };
    const closeEditPost = (post) => {
      post.isEditing = false;
    };

    return { posts, editPost, editPostButton, closeEditPost };
  },
};
</script>

<style>
.home {
  font-family: "Montserrat-Regular";
  padding: 20px;
}

.titleBlog {
  text-align: start;
  margin: 60px 40px;
}

.posts {
  margin-top: 50px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  gap: 30px;
}

.post {
  background-color: #fff;
  border-radius: 10px;
  padding: 30px;
}

.editing .editingButton,
.saveButton {
  cursor: pointer;
  background-color: #a970ee;
  border: 0;
  padding: 8px;
  border-radius: 5px;
  color: #fff;
  font-size: 12px;
  font-family: "Montserrat-Regular";
}

.editing .editingButton:hover {
  background-color: #5d4081;
}

.postCointainer .bodyPost {
  padding: 30px 0;
}

@media (max-width: 900px) {
  .posts {
    grid-template-columns: 1fr 1fr;
  }
}
</style>
