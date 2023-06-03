<template>
  <div>
    <h1>
      <a :href="link" @click.prevent="$emit('titleClick', title)">{{ title }}</a>
    </h1>
    <article>
      <div>
        {{ content.slice(0, 100) }}
      </div>
      <p>Total Viewer: {{ viewCount }}</p>
      <footer v-if="content.length > 100">
        <button>read more</button>
      </footer>
    </article>
    <slot></slot>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
defineProps(["title", "content", "link"]);
defineEmits(["titleClick"]);

const viewCount = ref(0);

onMounted(() => {
  setTimeout(()=>{
    viewCount.value = 100;
  }, 1000);
});
</script>