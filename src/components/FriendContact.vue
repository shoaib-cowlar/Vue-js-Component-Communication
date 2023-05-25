<template>
  <li>
    <h2>{{ friend.name }} {{ friend.isFavourite ? " (favourite) " : "" }}</h2>
    <button @click="toggleFavourite">Toggle favourite</button>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ friend.phone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ friend.email }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  props: {
    friend: {
      type: Object,
      required: true,
    },
  },
  emits: {
    "toggle-favourite": function (id) {
      if (id) {
        return true;
      } else {
        alert("id is missing for event");
        return false;
      }
    },
  },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
      this.$emit("toggle-favourite", this.friend.id);
    },
  },
};
</script>
