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
        'Cntct-main-panel',
        { ContactSmall: el.is.small, ContactMedium: el.is.medium },
      ]"
    >
      <div class="title-and-description">
        <h1 class="Cntct-main-title">Contact</h1>
        <p class="Cntct-description" v-html="data.mainText"></p>
      </div>
      <div class="Cntct-info-box">
        <div class="squarer">
          <div v-for="(item, index) in data.contactItems" :key="index" class="Cntct-info-item">
            <img class="logo" :src="item.logoUrl" />
            <a target="_blank" class="link" :href="item.linkUrl">
              {{
              item.contactMethod
              }}
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
  name: "Contact",
  props: {
    data: Object,
  },
  components: {
    Responsive,
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bungee+Inline&display=swap");
.Cntct-main-panel {
  display: flex;
  align-items: center;
}
.ContactSmall.Cntct-main-panel {
  flex-direction: column;
}
.title-and-description {
  display: flex;
  flex-direction: column;
  width: 50%;
  height: fit-content;
}
.ContactSmall .title-and-description {
  width: auto;
  margin: 0 10px;
}
.Cntct-main-title {
  font-family: "Bungee Inline", cursive;
  font-weight: normal;
  font-size: 3em;
  color: #00efab;
  text-align: start;
  text-shadow: 10px 10px 5px rgba(0, 0, 0, 0.5);
  margin: 5px 0;
}
.ContactSmall .Cntct-main-title {
  font-size: 2em;
  text-shadow: 10px 10px 5px rgba(0, 0, 0, 0.5);
}
.Cntct-description {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1em;
  font-weight: 100;
  white-space: pre-line;
  line-height: 140%;
  text-align: start;
  color: #b9faff;
}
.ContactMedium .Cntct-description {
  font-size: 0.9em;
}
.Cntct-info-box {
  border-style: dashed;
  border-width: 3px;
  border-color: #b2f9ff;
  border-radius: 7px;
  padding: 6px;
  margin-left: 10%;
  background-size: cover;
  background-clip: content-box;
  background-position: center;
  box-shadow: 0 10px 10px rgba(0, 0, 0, 0.5);
  position: relative;

  width: 50%;
  max-width: 350px;
}
.ContactSmall .Cntct-info-box {
  width: 75%;
  margin: 40px 0 0 0;
}
.Cntct-info-box .squarer {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 16px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.Cntct-info-box:after {
  content: "";
  display: block;
  padding-bottom: 100%;
}
.Cntct-info-item {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  border-top: 1px solid #00ddee;
  padding: 7% 0;
}
.Cntct-info-item:nth-of-type(1) {
  border: none;
}
.Cntct-info-item .logo {
  width: 9%;
  margin-right: 5%;
}
.Cntct-info-item .link {
  font-size: min(1.2em, 2.5vw);
  text-align: start;
  color: #00ddee;
  font-weight: 500;
}
.ContactSmall .Cntct-info-item .link {
  font-size: min(1.2em, 4vw);
}
</style>
