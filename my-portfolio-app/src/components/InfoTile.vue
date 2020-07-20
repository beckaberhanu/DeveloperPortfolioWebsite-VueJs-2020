<template>
  <Responsive
    :breakpoints="{
      small: (el) => el.width <= 570,
    }"
  >
    <div
      slot-scope="el"
      :class="['main-tile', { small: el.is.small, collapsed: collapsed }]"
    >
      <!-- <div :class="['main-tile']"> -->
      <div class="dash-border-image-box">
        <img :src="imageUrl" class="tile-image" />
      </div>
      <div :class="['text-content-container']">
        <div class="main-title">
          <h2>{{ mainTitle }}</h2>
          <img
            class="toggle-open-close-btn"
            :src="expandIcon"
            @click="expandTile()"
          />
        </div>
        <div :class="['collapsing-content']">
          <div class="tags">
            <div v-for="(tag, index) in tags" :key="index">
              <small>{{ tag }}</small>
              <div v-if="index < tags.length - 1" class="circle-spacer"></div>
            </div>
          </div>
          <div class="description">
            <p>{{ description }}</p>
          </div>
          <div class="external-links">
            <a
              v-for="(link, index) in externalLinks"
              :key="index"
              :href="link.url"
              target="_blank"
            >
              <object
                :data="link.icon"
                class="external-link-icon"
                type=""
              ></object>
              <small class="external-link-name">{{ link.name }}</small>
            </a>
          </div>
        </div>
      </div>
    </div>
  </Responsive>
</template>

<script>
import { Responsive } from "vue-responsive-components";
// import image1 from "../assets/images/minnehack-group-photo-2020.jpg";
import image1 from "../assets/images/minnehack-group-photo-2020-comp.jpg";
import image2 from "../assets/Icons/external-link.svg";
import image3 from "../assets/Icons/arrow.svg";

export default {
  name: "InfoTile",
  components: {
    Responsive,
  },
  data: function() {
    return {
      imageUrl: image1,
      mainTitle: "Minnehack: University of Minnesota Hackathon",
      expandIcon: image3,
      tags: ["Help local community", "Team work"],
      description:
        "Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore.",
      externalLinks: [
        {
          url: "https://minnehack.io/",
          icon: image2,
          name: "Minnehack",
        },
      ],
      collapsed: true,
    };
  },
  methods: {
    expandTile: function() {
      this.collapsed = this.collapsed ? false : true;
    },
  },
};
</script>

<style scoped>
.main-tile {
  display: flex;
  align-content: stretch;
  background-color: #162038;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.5);
  border-radius: 10px;
  padding: 12px;
}
.main-tile.small {
  flex-direction: column;
  position: relative;
}
.dash-border-image-box {
  flex: 1;
  display: flex;
  border-style: dashed;
  border-width: 3px;
  border-color: #b2f9ff;
  border-radius: 7px;
  padding: 7px;
  height: 280px;
  min-width: 280px;
}
.small .dash-border-image-box {
  height: 200px;
  width: auto;
}
.tile-image {
  object-fit: cover;
  border-radius: 5px;
  min-width: 200px;
  width: 100%;
  height: 100%;
}
.small .tile-image {
  min-width: none;
}
.text-content-container {
  display: flex;
  flex-direction: column;
  padding: 5px 25px;
  max-width: 50%;
}
.small .text-content-container {
  max-width: none;
  width: auto;
  padding: 8px 0px;
}
.small .text-content-container:not(.collapsed) {
  bottom: 0;
  background-color: #162038;
}
.main-title {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.main-title h2 {
  font-size: 1.7em;
  font-family: Arial, Helvetica, sans-serif;
  color: #00efab;
  text-align: start;
  margin: 0;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2; /* number of lines to show */
  -webkit-box-orient: vertical;
}
.small .main-title h2 {
  margin-right: 5px;
  font-size: 1.1em;
}
.toggle-open-close-btn {
  height: 20px;
  width: 20px;
  transform: rotate(90deg);
}
.main-tile:not(.small) .toggle-open-close-btn {
  display: none;
}
.collapsing-content {
  display: flex;
  flex-direction: column;
  flex: 1;
}
.tags {
  margin: 5px 0;
  display: flex;
}
.tags div {
  display: flex;
  align-items: center;
}
.tags small {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 0.8em;
  font-weight: 600;
  color: #465b8d;
}
.tags .circle-spacer {
  margin: 0 0.4em;
  border-radius: 0.2em;
  height: 0.4em;
  width: 0.4em;
  background-color: #465b8d;
}
.description {
  flex: 1;
  overflow-y: scroll;
}
.description p {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 0.9em;
  font-weight: 700;
  text-align: start;
  color: #fff;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 7; /* number of lines to show */
  -webkit-box-orient: vertical;
}
.small .description p {
  font-size: 0.7em;
}
.external-links {
  display: flex;
  align-self: flex-end;
  padding: 0;
}
.external-links a {
  display: flex;
  flex-direction: column;
  align-content: center;
  text-decoration: none;
}
.external-links a:hover {
  text-decoration: none;
}
.external-links a:visited {
  text-decoration: none;
}
.external-link-icon {
  height: 25px;
}
.external-link-name {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 0.5em;
  color: #646f8b;
}
</style>
