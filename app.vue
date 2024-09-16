<template>
  <div class="m-2 flex flex-col items-center">
    <Breadcrumbs :locale="locale" :tree="tree" @active="(value: number) => (active = value)" />
    <div class="flex">
      <ChangeLanguage @change="changeLocale" />
      <LinkPath class="ml-1" :tree="tree" :locale="locale" :active="active" />
    </div>
  </div>
</template>

<script setup lang="ts">
import {ref} from 'vue';

const info = useLoadData();
const tree = info[0].page_data.tree[0].path_to_top.reverse();

const locale = ref('ru');
const active = ref(tree.length - 1);

function changeLocale(value: string) {
  locale.value = value;
}
</script>
