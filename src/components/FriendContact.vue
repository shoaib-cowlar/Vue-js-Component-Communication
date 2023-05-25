<template>
  <li>
    <h2>{{ friend.name }} {{ isFavourite ? " (favourite) " : "" }}</h2>
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
    favourite: {
      type: Boolean,
    },
  },
  data() {
    return {
      detailsAreVisible: false,
      isFavourite: this.favourite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
      this.isFavourite = !this.isFavourite;
    },
  },
};
</script>
