<template>
  <div>
    <h1>Create a New Theatre</h1>
    <form @submit.prevent="createTheatre">
      <label>Name:</label>
      <input v-model="name" type="text" required />
      <br />
      <label>Address:</label>
      <input v-model="address" type="text" required />
      <br />
      <label>Admin ID:</label>
      <input v-model="admin_id" type="number" required />
      <br />
      <button type="submit">Create Theatre</button>
    </form>
  </div>
</template>

<script>
import api from "../api";
export default {
  data() {
    return {
      name: "",
      address: "",
      admin_id: "",
    };
  },
  methods: {
    async createTheatre() {
      try {
        const theatreData = {
          name: this.name,
          address: this.address,
          admin_id: this.admin_id,
        };
        await api.post("/theatres", theatreData);
        alert("Theatre created successfully!");
        this.$router.push("/theatres");
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
