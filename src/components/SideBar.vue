<template>
  <v-container fluid>
    <!-- <v-col cols="auto"> -->
    <v-card>
      <v-layout>
        <v-navigation-drawer expand-on-hover rail>
          <v-list>
            <v-list-item
              prepend-icon="mdi-home"
              title="Dashboard"
            ></v-list-item>
          </v-list>

          <v-divider></v-divider>

          <v-list density="compact" nav>
            <v-list-item
              prepend-icon="$vuetify"
              title="Companies"
              value="companies"
            ></v-list-item>
            <v-list-item
              prepend-icon="$vuetify"
              title="Departments"
              value="departments"
            ></v-list-item>
          </v-list>
        </v-navigation-drawer>

        <v-main style="height: 90vh">
          <AddCompany />
        </v-main>
      </v-layout>
    </v-card>
    <!-- </v-col> -->
  </v-container>
</template>
<script>
import AddCompany from "./AddCompany.vue";
export default {
  components: {
    AddCompany,
  },
};
</script>
