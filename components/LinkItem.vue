<template>
  <p v-if="index === lastIndex && item.locale[props.locale][props.cg] !== ''">{{ item.id }}_{{ item.locale[props.locale][props.cg] }}</p>
  <p v-else-if="index === lastIndex && item.locale[props.locale][props.cg] === '' && locale === 'en'">{{ item.id }}_{{ item.locale.ru[props.cg] }}</p>
  <p v-else-if="index === lastIndex && item.locale[props.locale][props.cg] === '' && locale === 'ru'">{{ item.id }}_{{ item.locale.en[props.cg] }}</p>
  <p v-else-if="item.locale[props.locale][props.cg] === '' && locale === 'en'">{{ item.locale.ru[props.cg] }}</p>
  <p v-else-if="item.locale[props.locale][props.cg] === '' && locale === 'ru'">{{ item.locale.en[props.cg] }}</p>
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
