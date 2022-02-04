<template>
  <input v-model="filter" placeholder="filter.." />
  <hr />
  <ul>
    <li v-for="item in filterest" :key="item.id">
      <slot name="header" :item="item"></slot>
    </li>
  </ul>
  <hr />
</template>

<script>
export default {
  data() {
    return {
      filter: "",
    };
  },
  props: {
    items: { type: Array, required: true },
    fields: { type: Array, required: true },
  },
  computed: {
    filterest() {
      return this.filter
        ? this.items.filter((u) =>
            this.fields.some((f) =>
              u[f].toLowerCase().includes(this.filter.toLowerCase())
            )
          )
        : this.items;
    },
  },
};
</script>

<style></style>
