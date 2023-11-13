<template>
  <div>
    <div class="addPost">
      <div class="headerAddPost">
        <h1>Add a new post...</h1>
        <div class="openModalButton">
          <span @click="openModalPost"><p>+</p></span>
        </div>
      </div>

      <div class="modalPost" v-if="openedModal">
        <header>
          <span @click="openModalPost">x</span>
        </header>
        <div class="modalContent">
          <h1>New Post</h1>
          <div class="titleAddPost">
            <h2>{{ title }}</h2>
            <input type="text" v-model="title" />
          </div>

          <div class="bodyAddPost">
            <textarea v-model="body" name="body" cols="50" rows="3"></textarea>
          </div>
          <div class="submit">
            <button @click="submitPost">Submit</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";

export default {
  props: ["posts"],
  name: "AddPostModal",

  setup(props) {
    const title = ref("Título");
    const body = ref("");
    let isEditing = ref(false);
    let openedModal = ref(false);

    const openModalPost = () => {
      openedModal.value = !openedModal.value;
    };

    const submitPost = () => {
      const newPost = {
        isEditing: isEditing.value,
        title: title.value,
        body: body.value,
      };

      props.posts.push(newPost);

      title.value = "Título";
      body.value = "";
      openModalPost();
    };

    return { title, body, openedModal, openModalPost, submitPost };
  },
};
</script>

<style>
.addPost {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.addPost .headerAddPost {
  display: flex;
  align-items: center;
}

.openModalButton span {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 29px;
  height: 35px;
  width: 35px;
  margin-left: 40px;
  background-color: #fa7c65;
  border-radius: 50%;
  color: #fff;
  cursor: pointer;
}

.openModalButton span:hover {
  background-color: #ba5341;
}

.modalPost {
  background-color: #fff;
  border-radius: 10px;
  margin: 40px;
  justify-content: center;
  max-width: 1350px;
}

.modalPost header {
  display: flex;
  justify-content: flex-end;
  color: #aaa;
  font-size: 20px;
  font-weight: bold;
  padding: 5px 10px 0 0;
}

.modalPost header span {
  cursor: pointer;
}

.modalPost header span:hover {
  color: #fa7c65;
}

.modalPost textarea {
  font-family: "Montserrat-Regular";
  width: 150px;
  height: 20px;
  transition: 0.3s ease-in-out;
}

.modalPost textarea:focus {
  width: 100%;
  height: 150px;
}

.modalContent {
  padding: 40px;
}
.modalContent .titleAddPost {
  padding: 40px 0;
}
.titleAddPost h2 {
  margin-bottom: 20px;
}
.bodyAddPost {
  margin-bottom: 20px;
}
.modalPost .submit button {
  cursor: pointer;
  background-color: #a970ee;
  border: 0;
  padding: 8px;
  border-radius: 5px;
  color: #fff;
  font-size: 12px;
  font-family: "Montserrat-Regular";
  font-weight: bold;
}
.modalPost .submit button:hover {
  background-color: #5d4081;
}
</style>
