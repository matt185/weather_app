<template>
  <v-container>
    <h1 class="text-caption-h1 d-flex justify-center">Weather App</h1>
    <v-flex>
      <v-card color="blue-grey darken-2">
        <v-card-text>card</v-card-text>
      </v-card>
    </v-flex>
    <v-flex class="d-flex justify-center mt-4">
      <v-form class="form">
        <v-text-field v-model="city" label="City Name" placeholder="city name" outlined></v-text-field>
      </v-form>
    </v-flex>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      city: ""
    };
  }
};
</script>

<style>
.form {
  width: 50%;
}
</style>