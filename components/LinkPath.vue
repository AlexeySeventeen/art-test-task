<template>
  <div class="flex">
    <h1 class="mr-1">Link:</h1>
    <!-- only parents -->
    <div v-if="active < tree.length" class="flex">
      <div v-for="(item, index) in tree">
        <div v-if="index <= active" class="flex">
          <LinkItem :locale="locale" :cg="'cg_slug'" :index="index" :item="item" :lastIndex="active" />
          <p class="mx-1">/</p>
        </div>
      </div>
    </div>
    <!-- with children -->
    <div v-else class="flex">
      <div v-for="(item, index) in tree.concat(treeChildren[active - tree.length])">
        <div class="flex">
          <LinkItem :locale="locale" :cg="'cg_slug'" :index="index" :item="item" :lastIndex="tree.length" />
          <p class="mx-1">/</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  locale: String,
  tree: Array,
  treeChildren: Array,
  active: Number,
});
</script>
