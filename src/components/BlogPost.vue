<template>
<div>
  <h1>
    <a :href="link">{{ title }}</a>
  </h1>
  <article>
    <div>
      {{ content.slice(0,100) }}
    </div>
    <footer v-if="content.length > 100">
      <button>read more</button>
    </footer>
  </article>
  <slot></slot>
</div>

</template>

<script setup>
    defineProps(["title", "content","link"]);
</script>