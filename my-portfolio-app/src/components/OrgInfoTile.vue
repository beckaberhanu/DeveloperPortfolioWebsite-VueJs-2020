<template>
  <Responsive
    :breakpoints="{
      small: (el) => el.width <= 700,
    }"
  >
    <div
      slot-scope="el"
      :class="['Org-main-panel', { OrgInfoTileSmall: el.is.small }]"
    >
      <div class="title-and-nav">
        <h1 class="main-title">{{ title }}</h1>
        <div class="scroll-nav">
          <!-- {{tileContent}} -->
          <div
            v-for="(tile, index) in tileContents"
            :key="index"
            class="nav-cell"
          >
            <div class="nav-bullet"></div>
            <p @click="findTile(title + '-' + index)">
              {{ tile.mainTitle }}
              <br />
            </p>
          </div>
        </div>
      </div>
      <div class="content-scroll">
        <!-- {{ tileContents }} -->
        <InfoTile
          v-for="(tileData, index) in tileContents"
          :key="index"
          :id="title + '-' + index"
          :data="tileData"
        />
        <!-- <InfoTile :id="title + '-' + '1'" /> -->
      </div>
    </div>
  </Responsive>
</template>
<script>
import InfoTile from "./InfoTile.vue";
import { Responsive } from "vue-responsive-components";

export default {
  name: "OrgInfoTile",
  props: {
    title: String,
    tileContents: Array,
  },
  components: {
    InfoTile,
    Responsive,
  },
  data: function() {
    return {
      // title: "Projects",
    };
  },
  methods: {
    findTile: function(id) {
      var tile = document.getElementById(id);
      var parent = tile.parentNode;
      this.scrollIntoView(parent, tile);
    },
    // ## https://medium.com/@vigu_madurai/solved-alternate-to-the-default-scrollintoview-8da76e083066
    scrollIntoView: function(parent, child) {
      const parentBounding = parent.getBoundingClientRect(),
        clientBounding = child.getBoundingClientRect();

      const parentBottom = parentBounding.bottom,
        parentTop = parentBounding.top,
        clientBottom = clientBounding.bottom,
        clientTop = clientBounding.top;

      if (parentTop >= clientTop) {
        this.scrollTo(parent, -(parentTop - clientTop), 100);
      } else if (clientBottom > parentBottom) {
        this.scrollTo(parent, clientBottom - parentBottom, 100);
      }
    },
    scrollTo: function(element, to, duration) {
      let start = element.scrollTop,
        currentTime = 0,
        increment = 20;

      function easeInOutQuad(time, startPos, endPos, duration) {
        time /= duration / 2;

        if (time < 1) return (endPos / 2) * time * time + startPos;
        time--;
        return (-endPos / 2) * (time * (time - 2) - 1) + startPos;
      }
      function animateScroll() {
        currentTime += increment;

        let val = easeInOutQuad(currentTime, start, to, duration);
        element.scrollTop = val;

        if (currentTime < duration) {
          setTimeout(animateScroll, increment);
        }
      }
      animateScroll();
    },
    // ** https://medium.com/@vigu_madurai/solved-alternate-to-the-default-scrollintoview-8da76e083066
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bungee+Inline&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Courier+Prime:ital,wght@0,400;0,700;1,400;1,700&display=swap");

.Org-main-panel {
  display: flex;
  max-height: 100%;
  width: 100%;
}
.OrgInfoTileSmall.Org-main-panel {
  flex-direction: column;
}
.title-and-nav {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  min-width: 22em;
  margin-right: 30px;
}
.OrgInfoTileSmall .title-and-nav {
  min-width: 0;
}
.main-title {
  font-family: "Bungee Inline", cursive;
  font-weight: unset;
  font-size: 3em;
  color: #00efab;
  text-shadow: 10px 10px 5px rgba(0, 0, 0, 0.5);
  margin: 25px 0;
}
.OrgInfoTileSmall .main-title {
  margin-left: 10px;
  margin-bottom: 0;
  font-size: 2em;
  /* text-shadow: 5px 5px 5px rgba(0, 0, 0, 0.5); */
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
  z-index: 0;
  left: 3px;
  top: 2em;
  bottom: 2em;
  border-left: 3px dashed #b2f9ff;
}
.content-scroll {
  max-height: 700px;
  padding: 10px;
  overflow-y: scroll;
  scroll-behavior: smooth;
  scroll-padding-top: 50px;
  scroll-margin-top: 50px;
  -webkit-mask-image: -webkit-linear-gradient(
    90deg,
    rgba(0, 0, 0, 0) 0%,
    rgba(0, 0, 0, 1) 5%,
    rgba(0, 0, 0, 1) 95%,
    rgba(0, 0, 0, 0) 100%
  );
}

.content-scroll::-webkit-scrollbar {
  width: 4px;
}

/* Track */
.content-scroll::-webkit-scrollbar-track {
  background: #00000000;
}

/* Handle */
.content-scroll::-webkit-scrollbar-thumb {
  background: #00000000;
}
.content-scroll:hover::-webkit-scrollbar-thumb {
  background: #003454;
  border-radius: 50px;
}
/* Handle on hover */
.content-scroll::-webkit-scrollbar-thumb:hover {
  background: #00efab;
}

.content-scroll {
  scrollbar-width: thin;
}

.OrgInfoTileSmall .content-scroll {
  max-height: max-content;
  padding: 10px;
  overflow-y: scroll;
  scroll-behavior: smooth;
  scroll-padding-top: 50px;
  scroll-margin-top: 50px;
}
.nav-cell {
  position: relative;
  display: flex;
  align-items: center;
  z-index: 2;
}
.nav-bullet {
  height: 10px;
  width: 10px;
  min-width: 10px;
  min-height: 10px;
  border-radius: 5px;
  background-color: #fff;
  box-shadow: 6px 6px 5px rgba(0, 0, 0, 0.5);
  transition: transform 0.4s;
  transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
}
.nav-cell p {
  font-family: "Courier Prime", monospace;
  font-size: 0.9em;
  color: #00ddee;
  text-shadow: 6px 6px 2px rgba(0, 0, 0, 1);
  text-align: start;
  transition: transform 0.4s;
  transform-origin: 0% 50%;
  transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
  margin: 17px 0 11px 10px;
}
.nav-cell:hover p {
  cursor: pointer;
  transform: translate(5px, 0) scale(1.1, 1.1);
  transform-origin: 0% 50%;
}
.nav-cell:hover .nav-bullet {
  transform: scale(1.4, 1.4);
}
</style>
