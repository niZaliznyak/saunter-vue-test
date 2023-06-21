<template>
  <v-dialog v-model="dialogVisible" width="auto">
    <v-card>
      <v-card-text>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
        tempor incididunt ut labore et dolore magna aliqua.
      </v-card-text>
      <v-card-actions>
        <v-btn color="primary" @click="dialogVisible = false">Close Dialog</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: {
    open: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      dialogVisible: false,
    };
  },
  watch: {
    open(newValue) {
      this.dialogVisible = newValue;
    },
    dialogVisible(newValue) {
      if (!newValue) {
        this.$emit("close");
      }
    },
  },
};
</script>
