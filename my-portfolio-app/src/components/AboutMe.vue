<template>
  <Responsive
    :breakpoints="{
      small: (el) => el.width <= 650,
      medium: (el) => el.width <= 800,
    }"
  >
    <div
      slot-scope="el"
      :class="[
        'Abt-main-panel',
        { AboutMeSmall: el.is.small, AboutMeMedium: el.is.medium },
      ]"
    >
      <div class="title-and-description">
        <h1 class="Abt-main-title">About Me</h1>
        <p class="Abt-description" v-html="data.mainText"></p>
      </div>
      <div
        class="Abt-image"
        :style="{
          'background-image':
            'linear-gradient(0deg,rgba(22, 32, 48, 1) 0%,rgba(25, 34, 58, 0.8029586834733894) 18%,rgba(105, 110, 126, 0) 43%,rgba(255, 255, 255, 0) 100%), url(' +
            remoteAssetsUrl +
            data.imageUrl +
            ')',
        }"
      >
        <small class="Abt-img-caption">
          <p v-html="data.imageCaption"></p>
        </small>
      </div>
    </div>
  </Responsive>
</template>

<script>
import { Responsive } from "vue-responsive-components";
export default {
  name: "AboutMe",
  props: {
    data: Object,
  },
  components: {
    Responsive,
  },
  data: function () {
    return {
      remoteAssetsUrl:
        "https://raw.githubusercontent.com/beckaberhanu/DeveloperPortfolioWebsite-VueJs-2020/master/my-portfolio-app/src/assets/",
    };
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bungee+Inline&display=swap");
.Abt-main-panel {
  display: flex;
  align-items: center;
}
.AboutMeSmall.Abt-main-panel {
  flex-direction: column;
}
.title-and-description {
  display: flex;
  flex-direction: column;
  width: 50%;
  height: fit-content;
}
.AboutMeSmall .title-and-description {
  width: auto;
  margin: 0 10px;
}
.Abt-main-title {
  font-family: "Bungee Inline", cursive;
  font-weight: normal;
  font-size: 3em;
  color: #00efab;
  text-align: start;
  text-shadow: 10px 10px 5px rgba(0, 0, 0, 0.5);
  margin: 5px 0;
}
.AboutMeSmall .Abt-main-title {
  font-size: 2em;
  text-shadow: 10px 10px 5px rgba(0, 0, 0, 0.5);
}
.Abt-description {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1em;
  font-weight: 100;
  white-space: pre-line;
  line-height: 140%;
  text-align: start;
  color: #b9faff;
}
.Abt-description >>> a {
  text-decoration: none;
  color: #00ddee;
  position: relative;
}
.Abt-description >>> a:visited {
  text-decoration: none;
}
.Abt-description >>> a:hover {
  text-decoration: none;
}
.Abt-description >>> a::after {
  content: "";
  position: absolute;
  bottom: 0px;
  left: 50%;
  height: 2px;
  width: 0;
  opacity: 0;
  background-color: #00ddee;
  transition: width 0.3s, left 0.3s, opacity 0.4s, margin-bottom 0.5s;
  transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
}
.Abt-description >>> a:hover::after {
  margin-bottom: -2px;
  width: 80%;
  left: 10%;
  opacity: 1;
}
.AboutMeMedium .Abt-description {
  font-size: 0.9em;
}
.Abt-image {
  border-style: dashed;
  border-width: 3px;
  border-color: #b2f9ff;
  border-radius: 7px;
  padding: 6px;
  margin-left: 40px;
  background-size: cover;
  background-clip: content-box;
  background-position: center;
  box-shadow: 0 10px 10px rgba(0, 0, 0, 0.5);
  position: relative;

  width: 50%;
  max-width: 500px;
}
.AboutMeSmall .Abt-image {
  width: 70%;
  margin: 40px 0 0 0;
}
.Abt-image:after {
  content: "";
  display: block;
  padding-bottom: 100%;
}
.Abt-img-caption {
  position: absolute;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 0.8em;
  font-weight: 100;
  text-align: start;
  color: #fff;
  bottom: 10px;
  left: 10px;
}
.Abt-img-caption >>> b {
  font-size: 100%;
  font-weight: 900;
  font-style: italic;
  color: #fff;
}
.Abt-img-caption p {
  font-size: 80%;
  font-weight: 100;
  margin: 3px 10px 3px 0;
  color: #e0e0e0;

  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>
