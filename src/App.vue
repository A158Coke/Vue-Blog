<script setup>
import { ref,computed } from "vue";


const blogs = ref([
  {
    id: 1,
    title: "Vue3 Try ",
    content: "This is my first try on Vue3 personally. Create a blog web page",
    link: "/vue-3-myblog",
  },
  {
    id: 2,
    title: "Test2 ",
    content: "This is my fry on Vue3 personally. Create a blog web page",
    link: "/vue-3-myblog",
  },
  {
    id: 3,
    title: "Test3 ",
    content: "This is my first try on Vue3 personally. Ceg ",
    link: "/vue-3-myblog",
  },
  {
    id: 4,
    title: "Test4",
    content: "This is my first n Vue3 personally. Create a blog  page",
    link: "/vue-3-myblog",
  },
 
]);

const total = computed(() => blogs.value.length);
const showTotal = ref(true);

 function toggleTotal (){
  showTotal.value = !showTotal.value;
 }

 const initialBlogForm = {
  title: "",
  content: "",
  link: "",
 };

 const blogForm = ref({ ...initialBlogForm });

 function addPost() {
  blogs.value.push({
    id: blogs.value.length + 1,
    ...blogForm.value,
  });
  blogForm.value = { ...initialBlogForm };
}
</script>

<template>
  <div v-for="blog in blogs" :key="blog.id">
  <h1>
    <a :href="blog.link">{{ blog.title }}</a>
  </h1>
  <article>
    <div>
      {{ blog.content }}
    </div>
    <footer v-if="blog.content.length > 100">
      <button>read more</button>
    </footer>
  </article>
</div>
<h3 v-if="showTotal">Total: {{ total }} blogs</h3>
<button @click="toggleTotal">{{ showTotal ? "Hide" : "Show" }} Total</button>
<form @submit.prevent="addPost">
  <label for="blogTitle">Title</label>
  <input type="text" id="blogTitle" v-model="blogForm.title">
  <label for="Content">Content</label>
  <textarea id="content" cols="30" rows="10" v-model="blogForm.content"></textarea>
  <label for="link" id="link">Link</label>
  <input type="text" id="link" v-model="blogForm.link">
  <button type="submit">Submit</button>
</form>
</template>

<style scoped>
form{
  display: grid;
  margin-top: 2em;
}
</style>
