<template>
  <div class="container">
    <h1 v-html="message"></h1>

    <!-- Image via CDN -->
    <img
      src="https://cdn-icons-png.flaticon.com/512/3774/3774299.png"
      width="120"
      alt="Blood Donor"
    />

    <h2>A+ Blood Group Donors</h2>

    <!-- Show only A+ donors -->
    <div v-for="donor in filteredDonors" :key="donor.name" class="card">
      <p><strong>Name:</strong> {{ donor.name }}</p>
      <p><strong>Blood:</strong> {{ donor.blood }}</p>
      <p><strong>City:</strong> {{ donor.city.toUpperCase() }}</p>

      <!-- Use v-show instead of v-if -->
      <p v-show="donor.available" class="available">
        Available for Donation
      </p>
    </div>

    <h3>Total Available Donors: {{ availableCount }}</h3>
  </div>
</template>

<script>
import donors from "./donors";

export default {
  data() {
    return {
      donors,
      message: "<span style='color:red'>Blood Donation App</span>",
    };
  },
  computed: {
    filteredDonors() {
      return this.donors.filter(d => d.blood === "A+");
    },
    availableCount() {
      return this.donors.filter(d => d.available).length;
    },
  },
};
</script>

<style>
.container {
  text-align: center;
  font-family: Arial;
}

.card {
  border: 1px solid #ddd;
  padding: 10px;
  margin: 10px;
}

.available {
  color: green;
  font-weight: bold;
}
</style>
