<template>
  <p v-if="index === lastIndex && props.item.locale[props.locale][props.cg] !== undefined">{{ item.id }}_{{ props.item.locale[props.locale][props.cg] }}</p>
  <p v-else-if="index === lastIndex && props.item.locale[props.locale][props.cg] === undefined && locale === 'en'">
    {{ item.id }}_{{ item.locale.ru[props.cg] }}
  </p>
  <p v-else-if="index === lastIndex && props.item.locale[props.locale][props.cg] === undefined && locale === 'ru'">
    {{ item.id }}_{{ item.locale.en[props.cg] }}
  </p>
  <p v-else-if="item.locale[props.locale][props.cg] === undefined && locale === 'en'">{{ item.locale.ru[props.cg] }}</p>
  <p v-else-if="item.locale[props.locale][props.cg] === undefined && locale === 'ru'">{{ item.locale.en[props.cg] }}</p>
  <p v-else>{{ item.locale[props.locale][props.cg] }}</p>
</template>

<script setup>
const props = defineProps({
  locale: String,
  cg: String,
  index: Number,
  lastIndex: Number,
  item: Object,
});
</script>
