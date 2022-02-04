<template>
  <input type="checkbox" :checked="footer.completed" />

  {{ footer.title }}
</template>

<script>
export default {
  props: {
    footer: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style></style>
