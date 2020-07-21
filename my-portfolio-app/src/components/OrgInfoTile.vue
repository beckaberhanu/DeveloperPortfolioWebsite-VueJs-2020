<template>
  <Responsive
    :breakpoints="{
      small: (el) => el.width <= 650,
    }"
  >
    <div
      slot-scope="el"
      :class="['Org-main-panel', { OrgInfoTileSmall: el.is.small }]"
    >
      <div class="title-and-nav">
        <h1 class="main-title">
          {{ title }}
        </h1>
        <div class="scroll-nav">
          <div class="nav-cell">
            <div class="nav-bullet"></div>
            <p @click="findTile(title + '-1')">Link to 1<br /></p>
          </div>
          <div class="nav-cell">
            <div class="nav-bullet"></div>
            <p @click="findTile(title + '-2')">Link to 2<br /></p>
          </div>
          <div class="nav-cell">
            <div class="nav-bullet"></div>
            <p @click="findTile(title + '-3')">Link to 3<br /></p>
          </div>
          <div class="nav-cell">
            <div class="nav-bullet"></div>
            <p @click="findTile(title + '-4')">Link to 4<br /></p>
          </div>
          <div class="nav-cell">
            <div class="nav-bullet"></div>
            <p @click="findTile(title + '-5')">Link to 5<br /></p>
          </div>
        </div>
      </div>
      <div class="content-scroll">
        <InfoTile :id="title + '-1'" />
        <InfoTile :id="title + '-2'" />
        <InfoTile :id="title + '-3'" />
        <InfoTile :id="title + '-4'" />
        <InfoTile :id="title + '-5'" />
      </div>
    </div>
  </Responsive>
</template>
<script>
import InfoTile from "./InfoTile.vue";
import { Responsive } from "vue-responsive-components";

export default {
  name: "OrgInfoTile",
  components: {
    InfoTile,
    Responsive,
  },
  data: function() {
    return {
      title: "Projects",
    };
  },
  methods: {
    findTile: function(id) {
      document.getElementById(id).scrollIntoView();
    },
  },
};
</script>
<style scoped>
.Org-main-panel {
  display: flex;
}
.OrgInfoTileSmall.Org-main-panel {
  flex-direction: column;
}
.title-and-nav {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  min-width: 300px;
}
.OrgInfoTileSmall .title-and-nav {
  min-width: 0;
}
.main-title {
  font-family: "Phosphate";
  font-weight: unset;
  font-size: 3.5em;
  color: #00ddef;
  text-shadow: 10px 10px 5px rgba(0, 0, 0, 0.5);
  margin: 25px 0;
}
.OrgInfoTileSmall .main-title {
  margin-left: 10px;
  font-size: 2em;
  text-shadow: 5px 5px 5px rgba(0, 0, 0, 0.5);
}
.scroll-nav {
  position: relative;
  margin-left: 15px;
}
.OrgInfoTileSmall .scroll-nav {
  display: none;
}
.scroll-nav::before {
  content: "";
  position: absolute;
  z-index: -1;
  left: 3px;
  top: 1.1em;
  bottom: 1.1em;
  border-left: 3px dashed #b2f9ff;
}
.content-scroll {
  height: 700px;
  padding: 10px;
  overflow-y: scroll;
  scroll-behavior: smooth;
  scroll-padding-top: 50px;
  scroll-margin-top: 50px;
}
.nav-cell {
  display: flex;
  align-items: center;
}
.nav-bullet {
  height: 10px;
  width: 10px;
  border-radius: 5px;
  background-color: #fff;
  box-shadow: 6px 6px 5px rgba(0, 0, 0, 0.5);
  transition: transform 0.4s;
  transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
}
.nav-cell p {
  font-family: "OCR A Std";
  font-size: 0.9em;
  color: #00efab;
  text-shadow: 6px 6px 5px rgba(0, 0, 0, 0.5);
  transition: transform 0.4s;
  transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
  margin: 17px 0 11px 10px;
}
.nav-cell:hover p {
  cursor: pointer;
  transform: translate(5px, 0);
}
.nav-cell:hover .nav-bullet {
  transform: scale(1.4, 1.4);
}
</style>
