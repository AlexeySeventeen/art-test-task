<template>
  <div class="flex">
    <div v-for="(item, index) in tree" :key="item.id" class="flex items-center">
      <div
        @click="(active = index), $emit('active', active)"
        class="cursor-pointer border rounded-lg py-1 px-2 hover:border-blue-500"
        :class="{'border-blue-300': index === active}">
        <LinkItem :locale="locale" :cg="'cg_name'" :index="index" :item="item" :lastIndex="tree.length - 1" />
      </div>
      <p class="mx-1 cursor-default">
        <svg fill="#000000" height="12px" width="12px" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 330 330">
          <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
          <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
          <g id="SVGRepo_iconCarrier">
            <path
              id="XMLID_222_"
              d="M250.606,154.389l-150-149.996c-5.857-5.858-15.355-5.858-21.213,0.001 c-5.857,5.858-5.857,15.355,0.001,21.213l139.393,139.39L79.393,304.394c-5.857,5.858-5.857,15.355,0.001,21.213 C82.322,328.536,86.161,330,90,330s7.678-1.464,10.607-4.394l149.999-150.004c2.814-2.813,4.394-6.628,4.394-10.606 C255,161.018,253.42,157.202,250.606,154.389z"></path>
          </g>
        </svg>
      </p>
    </div>

    <div class="flex flex-col gap-1">
      <div v-for="(item, index) in treeChildren" :key="item.id">
        <div
          @click="(active = index + tree.length), $emit('active', active)"
          class="cursor-pointer border rounded-lg py-1 px-2 hover:border-blue-500"
          :class="{'border-blue-300': index + tree.length === active}">
          <LinkItem :locale="locale" :cg="'cg_name'" :index="index" :item="item" :lastIndex="tree.length - 1" />
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import {ref} from 'vue';

const props = defineProps({
  locale: String,
  tree: Array,
  treeChildren: Array,
});

const emits = defineEmits(['active']);
const active = ref(props.tree.length - 1);
</script>
