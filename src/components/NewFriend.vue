<template>
  <form>
    <div>
      <label>ID</label>
      <input v-model="id" type="text" />

      <label>Name</label>
      <input v-model="name" type="text" />

      <label>Phone</label>
      <input v-model="phone" type="tel" />

      <label>E-Mail</label>
      <input v-model="email" type="email" />
      <button @click.prevent="submitData">Add Contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ["create-friend"],
  data() {
    return {
      id: "",
      name: "",
      phone: "",
      email: "",
    };
  },
  methods: {
    submitData() {
      const data = {
        id: this.id,
        name: this.name,
        email: this.email,
        phone: this.phone,
      };
      this.$emit("create-friend", data);
      this.id = "";
      this.name = "";
      this.phone = "";
      this.email = "";
    },
  },
};
</script>
<style>
#app input {
  font: inherit;
  padding: 0.15rem;
  width: 100%;
  margin: 10px 0;
}
#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}
#app form div {
  margin: 1rem 0;
}

#app form div button {
  margin: 1rem 0;
}
#app form {
  display: flex;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 20px;
  max-width: 40rem;
  max-height: 40rem;
  margin: 3rem auto;
}
</style>
