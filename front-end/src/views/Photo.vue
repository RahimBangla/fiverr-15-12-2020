<template>
  <div class="home">
    <br /><br />
    <br />
    <Images :photo="photo" />
    <p v-if="error">{{ error }}</p>
  </div>
</template>

<script>
import axios from "axios";
import Images from "@/components/Image.vue";
export default {
  name: "Home",
  components: {
    Images,
  },
  data() {
    return {
      photo: "",
      error: "",
    };
  },
  created() {
    this.getPhotos();
  },
  methods: {
    async getPhotos() {
      try {
        let response = await axios.get("/api/photos/" + this.$route.params.id);
        this.photo = response.data;
      } catch (error) {
        this.error = error.response.data.message;
      }
    },
  },
};
</script>

