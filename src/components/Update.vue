<template>
  <Header />
  <h1>Hello User, Welcome on Update Restaurant Page</h1>
  <form class="add" action="">
    <input
      type="text"
      name="name"
      placeholder="Enter Name"
      v-model="restaurant.name"
    />
    <input
      type="text"
      name="address"
      placeholder="Enter Address"
      v-model="restaurant.address"
    />
    <input
      type="text"
      name="contact"
      placeholder="Enter Contact"
      v-model="restaurant.contact"
    />
    <button v-on:click="updateRestaurant" type="button">
      Update restaurant
    </button>
  </form>
</template>
<script>
import axios from "axios";
import Header from "./Header.vue";
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Update",
  components: {
    Header,
  },
  data() {
    return {
      restaurant: {
        name: "",
        address: "",
        contact: "",
      },
    };
  },
  methods: {
    async updateRestaurant() {
      console.log(this.restaurant);
      const result = await axios.put(
        "http://localhost:3000/restaurants/" + this.$route.params.id,
        {
          name: this.restaurant.name,
          address: this.restaurant.address,
          contact: this.restaurant.contact,
        }
      );
      if (result.status == 200) {
        this.$router.push({ name: "Home" });
      }
    },
  },
  async mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }

    const result = await axios.get(
      "http://localhost:3000/restaurants/" + this.$route.params.id
    );
    console.log(result);
    this.restaurant = result.data;
  },
};
</script>
