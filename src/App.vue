<template>
  <v-app>
    <v-app-bar title="Saunter" color="blue-lighten-5">
      <v-btn
        variant="elevated"
        text="Add path"
        color="blue-lighten-1"
        @click="onClick"
      />
    </v-app-bar>
    <SideBar :paths="paths" @select="(id) => select(id)" :selected="selected" />
    <NewPathModal ref="newPathModelRef" />
    <v-main
      class="d-flex align-center justify-center"
      style="min-height: 300px"
    >
      Main Content
    </v-main>
  </v-app>
</template>

<script>
import SideBar from "./components/SideBar.vue";
import NewPathModal from "./components/NewPathModal.vue";

export default {
  data() {
    return {
      selected: null,
      paths: [
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
      openNewPathDialog: false,
    };
  },
  methods: {
    select(id) {
      this.selected = this.selected === id ? null : id;
    },
    onClick() {
      this.$refs.newPathModelRef?.open()
    },
  },
  components: {
    SideBar,
    NewPathModal,
  },
};
</script>
