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
        <h1 class="Abt-main-title">
          {{ title }}
        </h1>
        <p class="Abt-description">
          {{ description }}
        </p>
      </div>
      <div
        class="Abt-image"
        :style="{
          'background-image':
            'linear-gradient(0deg,rgba(22, 32, 48, 1) 0%,rgba(25, 34, 58, 0.8029586834733894) 18%,rgba(105, 110, 126, 0) 43%,rgba(255, 255, 255, 0) 100%), url(' +
            image1 +
            ')',
        }"
      >
        <small class="Abt-img-caption"
          ><h3>Caption</h3>
          {{ caption }}</small
        >
      </div>
    </div>
  </Responsive>
</template>

<script>
import { Responsive } from "vue-responsive-components";
import image1 from "../assets/images/SanFrancisco-beach-picture.jpg";
export default {
  name: "AboutMe",
  components: {
    Responsive,
  },
  data: function() {
    return {
      image1: image1,
      title: "AboutMe",
      description:
        "Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. \n\nLorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore.",
      caption: "Lorem ipsum dolor sit amet, consetetur sadipscing elitr",
    };
  },
};
</script>

<style scoped>
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
  width: 80%;
}
.Abt-main-title {
  font-family: "Phosphate";
  font-weight: unset;
  font-size: 3.5em;
  color: #00ddef;
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
  font-size: 1.2em;
  font-weight: 100;
  white-space: pre-line;
  line-height: 140%;
  text-align: start;
  color: #b9faff;
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
  width: 65%;
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
.Abt-img-caption h3 {
  font-size: 0.9em;
  font-weight: 700;
  font-style: italic;
  margin: 3px 0;
}
</style>
