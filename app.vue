<template>
  <div class="m-2 flex flex-col items-center">
    <Breadcrumbs :locale="locale" :tree="treeParents" :treeChildren="treeChildren" @active="(value: number) => (active = value)" />
    <div class="flex">
      <ChangeLanguage @change="changeLocale" />
      <LinkPath class="ml-1" :tree="treeParents" :treeChildren="treeChildren" :locale="locale" :active="active" />
    </div>
  </div>
</template>

<script setup lang="ts">
import {ref} from 'vue';

const info = useLoadData();
const treeParents = info[0].page_data.tree[0].path_to_top.reverse();
const treeChildren = info[0].page_data.tree[0].childs;

const locale = ref('ru');
const active = ref(treeParents.length - 1);

function changeLocale(value: string) {
  locale.value = value;
}
</script>
