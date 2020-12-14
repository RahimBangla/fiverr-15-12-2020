<template>
  <div>
    <section class="pure-u-1-1">
      <div class="image">
        <!-- <img :src="photo.path" /> -->
        <img :src="photo.path" />
        <div class="flex">
          <p class="userName pure-u-1-2">
            {{ photo.user.firstName }} {{ photo.user.lastName }}
          </p>
          <div class="left pure-u-1-12">
            <p class="photoDate">{{ formatDate(photo.created) }}</p>
          </div>
        </div>
      </div>
      <small> TITLE: </small>
      <br />
      <h1 class="photoTitle">{{ photo.title }}</h1>
      <div class="description">
        <small> DESCRIPTION: </small>
        <br /><br />
        {{ photo.description }}
      </div>
    </section>
  </div>
</template>

<script>
import moment from "moment";

export default {
  name: "Images",
  props: {
    photo: Array,
  },
  methods: {
    formatDate(date) {
      if (moment(date).diff(Date.now(), "days") < 15)
        return moment(date).fromNow();
      else return moment(date).format("d MMMM YYYY");
    },
  },
};
</script>

<style scoped>
.description {
  background-color: rgb(255, 247, 234);
  padding: 10px 15px 20px 15px;
  margin-bottom: 100px;
  border: 1px solid black;
  border-radius: 10px;
}

.userName {
  color: black;
}
.photoTitle {
  font-size: 35px;
  text-transform: uppercase;
  color: #0043ff;
  padding: 0px 25px 1px 25px;
  margin: 0;
}
.photoInfo {
  display: flex;
  justify-content: space-between;
  font-size: 0.8em;
}
.flex {
  display: flex;
}
.photoInfo p {
  margin: 0px;
}
.left {
  text-align: right;
  vertical-align: right;
  width: 100%;
}
.photoDate {
  font-size: 0.9em;
  font-weight: normal;
  text-align: end;
}

p {
  margin: 0px;
}

/* Masonry */
*,
*:before,
*:after {
  box-sizing: inherit;
}

.images {
  column-gap: 1em;
}

.image {
  display: inline-block;
  width: 100%;
}

.image img {
  width: 100%;
}

/* Masonry on large screens */
@media only screen and (min-width: 1024px) {
  .images {
    column-count: 1;
  }
}

/* Masonry on medium-sized screens */
@media only screen and (max-width: 1023px) and (min-width: 768px) {
  .images {
    column-count: 1;
  }
}

/* Masonry on small screens */
@media only screen and (max-width: 767px) and (min-width: 540px) {
  .images {
    column-count: 1;
  }
}
</style>