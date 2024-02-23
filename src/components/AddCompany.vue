<template>
  <div>
    <v-container>
      <v-row justify="end">
        <v-col cols="auto">
          <v-btn color="primary" @click="showDialog">Add Company</v-btn>
        </v-col>
      </v-row>
    </v-container>
    <!-- <v-btn color="primary" @click="showDialog" class="button"
      >Add Company</v-btn
    > -->
    <v-dialog v-model="dialog" max-width="500px">
      <v-card>
        <v-card-title> Enter Details </v-card-title>
        <v-card-text>
          <v-text-field
            v-model="companyName"
            label="Company Name"
          ></v-text-field>
          <v-text-field v-model="email" label="Email"></v-text-field>
          <v-text-field v-model="user" label="User"></v-text-field>
          <v-text-field
            v-model="description"
            label="Description"
          ></v-text-field>
          <!-- Add more input fields as needed -->
        </v-card-text>
        <v-card-actions>
          <v-btn color="primary" @click="saveAndClose">Save</v-btn>
          <v-btn @click="closeDialog">Close</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      companyName: "",
      email: "",
      user: "",
      description: "",
      // Add more data properties for additional input fields
    };
  },
  methods: {
    showDialog() {
      this.dialog = true;
    },
    closeDialog() {
      this.dialog = false;
    },
    saveAndClose() {
      // Here you can handle saving the input data
      console.log("Name:", this.companyName);
      console.log("Email:", this.email);
      console.log("User", this.user);
      console.log("Description", this.description);
      // Close the dialog
      this.dialog = false;
      // Optionally, you can perform further actions like saving data to a backend server
    },
  },
};
</script>

<style scoped>
.button {
  top: 20px;
  right: 20px;
}
</style>
