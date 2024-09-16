<template>
  <div class="flex">
    <h1 class="mr-1">Link:</h1>
    <div v-for="(item, index) in tree">
      <div v-if="index <= active" class="flex">
        <LinkItem :locale="locale" :cg="'cg_slug'" :index="index" :item="item" :lastIndex="active" />
        <p class="mx-1">/</p>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  locale: String,
  tree: Array,
  active: Number,
});
</script>
