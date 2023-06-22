<template>
  <v-navigation-drawer permanent>
    <v-text-field
      v-model="search"
      label="Search"
      placeholder="Search..."
      variant="outlined"
      hide-details
      append-inner-icon="mdi-magnify"
      class="ma-3"
    ></v-text-field>
    <v-list lines="two">
      <v-list-item
        v-for="path in filteredPaths"
        :key="path.id"
        :title="path.title"
        :subtitle="path.shortDescription"
        @click="$emit('select', path.id)"
     
        :class="{ 'bg-blue': path.id === selected, 'pa-1 ma-1': true }"
        style="cursor: pointer"
        rounded
        border
      >
        <template v-slot:prepend>
          <v-avatar>
            <v-icon icon="mdi-arrow-expand-all"></v-icon>
          </v-avatar>
        </template>
        <template v-slot:append>
          <v-icon icon="mdi-chevron-right"></v-icon>
        </template>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  emits: ['select'],
  props: ["paths", "selected"],
  data() {
    return {
      search: "",
    };
  },
  computed: {
    filteredPaths() {
      return this.search
        ? this.paths.filter((path) => {
            const { title, shortDescription } = path;

            return (
              title.toLowerCase().includes(this.search.toLowerCase()) ||
              shortDescription.toLowerCase().includes(this.search.toLowerCase())
            );
          })
        : this.paths;
    },
  },
};
</script>
