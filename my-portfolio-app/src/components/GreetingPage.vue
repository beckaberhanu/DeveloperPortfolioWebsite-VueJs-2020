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
        'Grt-main-panel',
        { GreetingSmall: el.is.small, GreetingMedium: el.is.medium },
      ]"
    >
      <div class="layer-1">
        <h1 class="greeting-message">
          <span class="t1">Hi &nbsp;</span>
          <span class="t2">there! I'm</span>
          <br />
          <span class="t3">BECKA GELETO</span>
        </h1>
        <div class="box-nav-panel">
          <h2 class="nav-title">Welcome to my Portfolio</h2>
          <div class="introduction">
            <p>
              The following sections contain a highlight of some of my
              experience a computer science student and enthuthiast. I’ve
              included my past and present projects, extra curricular
              activities, relevant courses and skills.
            </p>
            <p>
              To anyone who has any questions, tips, suggestions about the
              content or format of this web site I highly encourage you to
              <a href="#contact-section">reach out</a> to me.
            </p>
          </div>
          <div class="nav-btns">
            <div>
              <a href="#about-me-section">About Me</a>
            </div>
            <div>
              <a href="#project-section">Project</a>
            </div>
            <div>
              <a href="#activities-section">Activities</a>
            </div>
            <div>
              <a href="#contact-section">Contact</a>
            </div>
          </div>
          <div class="contact-info">
            <img :src="remoteAssetsUrl + 'Icons/linkedin.svg'" />
            <img :src="remoteAssetsUrl + 'Icons/gmail.svg'" />
            <img :src="remoteAssetsUrl + 'Icons/github-logo.svg'" />
          </div>
        </div>
      </div>
      <div class="layer-2">
        <div class="Grt-cover"></div>
        <div class="Grt-btm-cover"></div>
        <img
          class="Grt-bkg-image"
          :src="
            remoteAssetsUrl + 'images/{Misc}SaintPaulCityPictureMin[Mid].jpg'
          "
        />
      </div>
    </div>
  </Responsive>
</template>

<script>
import { Responsive } from "vue-responsive-components";

export default {
  name: "GreetingPage",
  components: {
    Responsive,
  },
  data: function() {
    return {
      remoteAssetsUrl:
        "https://raw.githubusercontent.com/beckaberhanu/DeveloperPortfolioWebsite-VueJs-2020/master/my-portfolio-app/src/assets/",
    };
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bungee+Inline&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Courier+Prime:ital,wght@0,400;0,700;1,400;1,700&display=swap");

.Grt-main-panel {
  height: 100%;
  width: 100%;
  padding: 0;
  margin: 0;
  position: relative;
}
.layer-1 {
  position: absolute;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-end;
}
.greeting-message {
  text-shadow: 10px 10px 5px rgba(0, 0, 0, 0.5);
  margin-left: 20px;
  text-align: start;
  align-self: flex-start;
}
.greeting-message .t1 {
  font-family: "Bungee Inline", cursive;
  font-weight: normal;
  font-size: 2em;
  color: #00ddef;
}
.greeting-message .t2 {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.2em;
  color: #fff;
}
.greeting-message .t3 {
  font-family: "Bungee Inline", cursive;
  font-weight: normal;
  font-size: 3em;
  color: #00efab;
}
.GreetingSmall .greeting-message {
  bottom: 40%;
  left: 0;
  text-shadow: 5px 5px 5px rgba(0, 0, 0, 0.5);
}
.GreetingSmall .greeting-message .t1 {
  font-size: 8vw;
}
.GreetingSmall .greeting-message .t2 {
  font-size: 5vw;
}
.GreetingSmall .greeting-message .t3 {
  font-size: 10vw;
}
.box-nav-panel {
  display: flex;
  flex-direction: column;

  background-color: #162038;
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.5);
  border-radius: 10px;
  align-self: stretch;
  margin: 0 25px 25px 25px;
  padding: 30px;

  position: absolute;
  width: 40%;
  max-width: 400px;
  min-width: 360px;
  right: 7%;
  bottom: 100px;
}
.GreetingMedium .box-nav-panel {
  display: none;
}
.GreetingSmall .box-nav-panel {
  position: unset;
  width: unset;
  display: flex;
  min-height: 30%;
  max-width: unset;
  min-width: unset;
}
.nav-title {
  font-family: Arial, Helvetica, sans-serif;
  font-size: min(2em, 5vw);
  font-weight: 900;
  text-align: start;
  color: #00efab;
  margin-top: 0;
}
.introduction {
  border-left: 5px solid #00efab;
  margin-bottom: 0.83em;
}
.GreetingSmall .introduction {
  display: none;
}
.introduction p {
  font-family: "Courier Prime", monospace;
  font-weight: 400;
  font-size: 1.9vh;
  text-align: left;
  color: #fff;
  margin: 10px 0 2px 10px;
  line-height: 2.6vh;
}
.introduction p:nth-of-type(1) {
  margin-top: 2px;
}
.introduction p >>> a {
  text-decoration: none;
  color: #00ddee;
  position: relative;
}
.introduction p >>> a:visited {
  text-decoration: none;
}
.introduction p >>> a:hover {
  text-decoration: none;
}
.introduction p >>> a::after {
  content: "";
  position: absolute;
  bottom: 0px;
  left: 50%;
  height: 2px;
  width: 0;
  opacity: 0;
  background-color: #00ddee;
  transition: width 0.3s, left 0.3s, opacity 0.4s;
  transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
}
.introduction p >>> a:hover::after {
  width: 80%;
  left: 10%;
  opacity: 1;
}
.nav-btns {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  flex: 1;
}
.nav-btns div {
  width: 45%;
  padding: 10px 0;
  border: 2px solid #00ddee;
  border-radius: 5px;
  color: #00ddee;
  margin: 10px 0;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
.nav-btns a {
  text-decoration: none;
  color: #00ddee;
  font-family: Arial, Helvetica, sans-serif;
  font-size: min(1.3em, 5vw);
  font-weight: 700;
  text-align: center;
  line-height: min(1.3em, 5vw);
}
.nav-btns a:hover {
  text-decoration: none;
}
.nav-btns a:visited {
  text-decoration: none;
}
.contact-info {
  display: flex;
  justify-content: flex-start;
  margin-top: 15px;
}
.contact-info img {
  height: 4vh;
  margin-right: 25px;
}

.layer-2 {
  height: 100%;
  width: 100%;
  position: relative;
  display: flex;
  align-items: center;
  z-index: -1;
}
.GreetingSmall .layer-2 {
  flex-direction: column;
  overflow: hidden;
}
.Grt-cover {
  height: 100%;
  width: 50%;
  background-image: radial-gradient(
    ellipse farthest-side at 30% 30%,
    rgba(22, 34, 52, 0) 0%,
    rgba(27, 34, 52, 0.83) 75%,
    rgba(27, 34, 52, 1) 100%
  );
  min-width: 600px;
}
.GreetingSmall .Grt-cover {
  width: 120%;
  height: 65%;
  min-width: 0;
  background-image: radial-gradient(
    ellipse farthest-side at 50% 20%,
    rgba(27, 34, 52, 0) 0%,
    rgba(27, 34, 52, 0.83) 77%,
    #1b2234 100%
  );
}
.GreetingSmall .Grt-btm-cover {
  height: 35%;
  width: 100%;
  background-color: #1b2234;
}
.Grt-bkg-image {
  height: 100%;
  width: 50%;
  position: fixed;
  left: 0;
  bottom: 0;
  z-index: -1;
  overflow: hidden;
  object-fit: cover;
  object-position: center;
  min-width: 600px;
}
.GreetingSmall .Grt-bkg-image {
  width: 100%;
  height: 60%;
  min-width: 0;
  left: 0;
  top: 0;
}
</style>
