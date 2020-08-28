<template>
  <Responsive :breakpoints="{
      small: (el) => el.width <= 570,
    }">
    <div
      slot-scope="el"
      :class="[
        'main-tile',
        {
          InfoTileSmall: el.is.small,
          collapsed: collapsed,
          interacted: interacted,
        },
      ]"
    >
      <div class="dash-border-image-box">
        <img :src="data.imageUrl" class="tile-image" />
      </div>
      <div :class="['text-content-container']">
        <div class="main-title" @click="expandTile()">
          <h2>{{ data.mainTitle }}</h2>
          <img class="toggle-open-close-btn" src="Static/Icons/arrow.svg" />
        </div>
        <div :class="['collapsing-content']">
          <div class="tags">
            <div v-for="(tag, index) in data.tags" :key="index">
              <small>{{ tag }}</small>
              <div v-if="index < data.tags.length - 1" class="circle-spacer"></div>
            </div>
          </div>
          <div class="description">
            <p v-html="data.description"></p>
            <p v-if="data.teamMates.length > 0" class="team-mates">TeamMates
              <ul>
                <li v-for="(teamMate, index) in data.teamMates" :key="index" style="color:#fff;">
                  {{teamMate.name}}
                  <a v-if="teamMate.link" :href="teamMate.link" target="_blank">
                    <img
                      :src="teamMate.icon"
                    />
                  </a>
                </li>
              </ul>
            </p>
          </div>
          <div class="external-links">
            <a
              v-for="(link, index) in data.externalLinks"
              :key="index"
              :href="link.url"
              target="_blank"
            >
              <img :src="link.icon" class="external-link-icon" />
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

export default {
  name: "InfoTile",
  props: {
    anchor: String,
    data: Object,
  },
  components: {
    Responsive,
  },
  data: function () {
    return {
      expandIcon: "Icons/arrow.svg",
      collapsed: true,
      interacted: false,
    };
  },
  methods: {
    expandTile: function () {
      this.collapsed = this.collapsed ? false : true;
      this.interacted = true;
    },
  },
};
</script>

<style scoped>
.main-tile {
  display: flex;
  align-content: stretch;
  background-color: #162038;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 1);
  border-radius: 10px;
  padding: 12px;
  margin: 25px 0px;
  height: 40%;
}
.main-tile.InfoTileSmall {
  flex-direction: column;
  position: relative;
  height: 270px;
  overflow: hidden;
  transition: padding-top 0.4s, height 0.4s;
  transition-timing-function: cubic-bezier(0.95, 0.05, 0.795, 0.035);
}
.main-tile.InfoTileSmall:not(.collapsed) {
  padding-top: 0;
  height: 282px;
}
.dash-border-image-box {
  flex: 1;
  display: flex;
  border-style: dashed;
  border-width: 3px;
  border-color: #b2f9ff;
  border-radius: 7px;
  padding: 7px;
  /* height: 100%; */
  /* height: 280px; */
  min-width: 50%;
}
.InfoTileSmall .dash-border-image-box {
  flex: none;
  height: 200px;
  width: auto;
}
.InfoTileSmall:not(.collapsed) .dash-border-image-box {
  height: 0;
  opacity: 0;
  padding: 0;
  border-width: 0px;
  animation: expandAnim 0.8s cubic-bezier(0.19, 1, 0.22, 1);
}
@keyframes expandAnim {
  0% {
    height: 200px;
    padding: 7px;
    opacity: 1;
    border-width: 3px;
  }
  100% {
    height: 0px;
    padding: 0px;
    opacity: 0;
    border-width: 0px;
  }
}
.InfoTileSmall.collapsed.interacted .dash-border-image-box {
  height: 200px;
  opacity: 1;
  padding: 7px;
  border-width: 3px;
  animation: collapseAnim 0.8s cubic-bezier(0.19, 1, 0.22, 1);
}
@keyframes collapseAnim {
  0% {
    height: 0px;
    padding: 0px;
    opacity: 0;
    border-width: 0px;
  }
  100% {
    height: 200px;
    padding: 7px;
    opacity: 1;
    border-width: 3px;
  }
}
.tile-image {
  object-fit: cover;
  border-radius: 5px;
  min-width: 200px;
  width: 100%;
  height: 100%;
}
.InfoTileSmall .tile-image {
  min-width: 0;
}
.text-content-container {
  display: flex;
  flex-direction: column;
  padding: 5px 5px 5px 25px;
  max-width: 50%;
}
.InfoTileSmall .text-content-container {
  max-width: none;
  width: auto;
  padding: 8px 0px;
  flex: none;
}
.InfoTileSmall .text-content-container:not(.collapsed) {
  background-color: #162038;
}
.main-title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 3.4em;
}
.main-title h2 {
  font-size: 1.4em;
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
.InfoTileSmall .main-title h2 {
  margin-right: 5px;
  font-size: 1.1em;
}
.toggle-open-close-btn {
  height: 20px;
  width: 20px;
  transform: rotate(90deg);
}
.main-tile:not(.InfoTileSmall) .toggle-open-close-btn {
  display: none;
}
.InfoTileSmall.collapsed .toggle-open-close-btn {
  transform: rotate(270deg);
}
.collapsing-content {
  display: flex;
  flex-direction: column;
  flex: 1;
  min-height: 0;
}
.InfoTileSmall .collapsing-content {
  height: 215px;
  flex: none;
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
  color: #ff4390;
}
.tags .circle-spacer {
  margin: 0 0.4em;
  border-radius: 0.2em;
  height: 0.4em;
  width: 0.4em;
  background-color: #fff;
}
.description {
  flex: 1;
  overflow-y: scroll;
  -webkit-mask-image: -webkit-linear-gradient(
    90deg,
    rgba(0, 0, 0, 0) 0%,
    rgba(0, 0, 0, 1) 5%,
    rgba(0, 0, 0, 1) 95%,
    rgba(0, 0, 0, 0) 100%
  );
}
.description p {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 0.9em;
  font-weight: 700;
  text-align: start;
  color: #fff;
}
.InfoTileSmall .description p {
  font-size: 0.8em;
}
p.team-mates {
  color: #00eca9;
  margin-left: 20px;
}
.team-mates ul {
  margin: 0 0 0 20px;
  list-style-type: square;
  padding: 0;
}
.team-mates li{
  margin: 4px 0;
}
.team-mates img {
  height: 1.1em;
}
.team-mates a{
  border-bottom: 1px solid #00ddee;
}
.external-links {
  display: flex;
  align-self: flex-end;
  padding: 0 0px;
}
.external-links a {
  display: flex;
  margin: 0 10px;
  flex-direction: column;
  align-content: center;
  text-decoration-line: underline;
  text-decoration-color: #00ddee;
}
.external-links a:hover {
  text-decoration-line: underline;
  text-decoration-color: #00ddee;
}
.external-links a:visited {
  text-decoration-line: underline;
  text-decoration-color: #00ddee;
}
.external-link-icon {
  height: 25px;
  animation-name: attention;
  transition: transform 0.3s;
  transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
  /* animation-iteration-count: infinite;
  animation-duration: 7s;
  animation-timing-function: linear; */
}
.external-links a:hover .external-link-icon {
  animation: none;
  transform: translateY(-6px);
}

@keyframes attention {
  0% {
    transform: translateY(0);
  }
  3% {
    transform: translateY(0);
  }
  6% {
    transform: translateY(-4px);
  }
  9% {
    transform: translateY(0);
  }
  12% {
    transform: translateY(-4px);
  }
  100% {
    transform: translateY(0);
  }
}
.external-link-name {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 0.5em;
  margin-top: 3px;
  color: #00ddee;
}
</style>
