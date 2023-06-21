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
        v-for="(item, i) in searchedItems"
        :key="i"
        :title="item.title"
        :subtitle="item.shortDescription"
        @click.stop="select(item.id)"
        class="pa-1 ma-1"
        :class="{'bg-blue' : item.id === selected}"
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
let id = 0;
export default {
  data() {
    return {
      search: "",
      selected: null,
      items: [
        {
          id: 1,
          title: "Path title 12",
          shortDescription: "Short description 1",
          pathlength: "1000km",
        },
        {
          id: 2,
          title: "Path title 2",
          shortDescription: "Short description 2",
          pathlength: "2000km",
        },
      ],
    };
  },
  methods: {
    select(id) {
      this.selected = id
    }
  },
  computed: {
    searchedItems() {
      return this.search
        ? this.items.filter((item) => {
            const { title, shortDescription } = item;

            return (
              title.toLowerCase().includes(this.search.toLowerCase()) ||
              shortDescription.toLowerCase().includes(this.search.toLowerCase())
            );
          })
        : this.items;
    },
  },
};
</script>
