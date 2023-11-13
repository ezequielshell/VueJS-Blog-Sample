<template>
  <div class="background">
    <div class="EditPost">
      <h1>{{ props.post.title }}</h1>
      <p>{{ props.post.body }}</p>
      <div class="titleEditPost">
        <input type="text" v-model="props.post.title" />
      </div>
      <div class="body">
        <textarea
          name="body"
          cols="40"
          rows="3"
          v-model="props.post.body"
        ></textarea>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["post"],
  setup(props) {
    return { props };
  },
};
</script>

<style>
.body,
.EditPost p {
  padding: 20px 0;
}

.body textarea {
  font-family: "Montserrat-Regular";
  width: 150px;
  height: 40px;
  transition: 0.3s ease-in-out;
}

.body textarea:focus {
  width: 100%;
  height: 130px;
}
</style>
