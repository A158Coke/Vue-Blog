<template>
<div>
  <h1>
    <a :href="link">{{ title }}</a>
  </h1>
  <article>
    <div>
      {{ content }}
    </div>
    <footer v-if="blog.content.length > 100">
      <button>read more</button>
    </footer>
  </article>
</div>

</template>

<script setup>
    defineProps(["title", "content","link"]);
</script>