<template>
  <v-dialog v-model="dialogVisible" width="800px">
    <v-card>
      <v-card-title>
        <span class="text-h5">Add new path</span>
      </v-card-title>
      <v-container>
        <v-row>
          <v-col cols="12" sm="6">
            <v-form @submit.prevent>
              <v-text-field
                variant="outlined"
                v-model="title"
                :rules="[(v) => required(v, 'title')]"
                label="Title"
              ></v-text-field>
              <v-textarea
                variant="outlined"
                counter
                no-resize
                rows="2"
                :rules="[(v) => required(v, 'shortDescription')]"
                v-model="shortDescription"
                label="Short description"
              ></v-textarea>
              <v-textarea
                variant="outlined"
                no-resize
                :rules="[(v) => required(v, 'fullDescription')]"
                v-model="fullDescription"
                label="Full description"
              ></v-textarea>
              <v-btn
                type="submit"
                variant="outlined"
                block
                class="mt-2"
                @click="close"
                >Add path</v-btn
              >
            </v-form>
          </v-col>
          <v-col cols="12" sm="6">
            <v-sheet class="ma-2 pa-2"> Map </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data() {
    return {
      dialogVisible: false,
      title: "",
      shortDescription: "",
      fullDescription: "",
    };
  },
  methods: {
    open() {
      this.dialogVisible = true;
    },
    close() {
      this.dialogVisible = false;
    },
    onSubmit() {
      if (!this.form) return;
    },
    required(value, key) {
      if (key !== "shortDescription") {
        return !!value || "Field is required";
      } else {
        if (value.length > 160) {
          return "Please enter a shorter description";
        } else if (!value) {
          return "Field is required";
        }
      }
      return true;
    },
  },
};
</script>
