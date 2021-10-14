<template>
  <div id="app">
    <nav class="top-nav-bar">
      <a href="#greeting-section" class="back-to-top">
        <h1 class="site-logo">Becka Geleto</h1>
      </a>
      <div :class="['nav-sections', { closed: !menuOpened }]">
        <a class="nav-section" href="#about-me-section">About Me</a>
        <a class="nav-section" href="#experience-section">Experience</a>
        <a class="nav-section" href="#project-section">Projects</a>
        <a class="nav-section" href="#activities-section">Activities</a>
        <a class="nav-section" href="#contact-section">Contact</a>
        <a
          class="nav-section resume-btn"
          target="_blank"
          href="/Static/Files/BeckaGeleto-Resume.pdf"
        >Resume ⤓</a>
      </div>
      <div class="hamburger-button" @click="toggleMenu()">
        <img src="/Static/Icons/open-menu.svg" />
      </div>
    </nav>
    <div id="greeting-section" style="height:0px; width:100px;"></div>
    <section class="greeting-section">
      <GreetingPage
        :WelcomeMessage="greetingPage.WelcomeMessage"
        :contactInfo="contact.contactItems"
      />
    </section>
    <div id="about-me-section" style="height:0px; width:100px;"></div>
    <section class="about-me-section">
      <div class="left-side-spacer v1">
        <h1>AboutMe</h1>
      </div>
      <div class="section-content">
        <AboutMe :data="aboutMe" />
      </div>
      <div class="right-side-spacer"></div>
    </section>
    <div id="experience-section" style="height:0px; width:100px;"></div>
    <section class="experience-section stacking-slide">
      <div class="left-side-spacer v2">
        <span class="vertical-text-container">
          <h1>Experience</h1>
        </span>
      </div>
      <div class="section-content">
        <org-info-tile title="Experience" :tileContents="workExperience" />
      </div>
      <div class="right-side-spacer"></div>
    </section>
    <div id="project-section" style="height:0px; width:100px;"></div>
    <section class="project-section stacking-slide">
      <div class="left-side-spacer v1">
        <span class="vertical-text-container">
          <h1>Projects</h1>
        </span>
      </div>
      <div class="section-content">
        <org-info-tile title="Projects" :tileContents="projects" />
      </div>
      <div class="right-side-spacer"></div>
    </section>
    <div id="activities-section" style="height:0px; width:100px;"></div>
    <section class="activities-section stacking-slide">
      <div class="left-side-spacer v2">
        <span class="vertical-text-container">
          <h1>Activities</h1>
        </span>
      </div>
      <div class="section-content">
        <org-info-tile title="Activities" :tileContents="activities" />
      </div>
      <div class="right-side-spacer"></div>
    </section>
    <div id="contact-section" style="height:0px; width:100px;"></div>
    <section class="contact-section stacking-slide">
      <div class="left-side-spacer v1">
        <span class="vertical-text-container">
          <h1>Contact</h1>
        </span>
      </div>
      <div class="section-content">
        <Contact :data="contact" />
      </div>
      <div class="right-side-spacer"></div>
    </section>
    <div class="about-webpage">
      <p>
        Designed and Developed by:
        <b>Becka Geleto</b>
      </p>
      <p>
        Built using:
        <b>Vue.js</b>
      </p>
      <p>
        Inspired by:
        <b>Brittany Chang, brittanychiang.com/</b>
      </p>
      <p>
        Hosted on:
        <b>Github Pages</b>
      </p>
    </div>
  </div>
</template>

<script>
import GreetingPage from "./components/GreetingPage.vue";
import AboutMe from "./components/AboutMe.vue";
import OrgInfoTile from "./components/OrgInfoTile.vue";
import Contact from "./components/Contact.vue";

export default {
  name: "App",
  components: {
    OrgInfoTile,
    AboutMe,
    GreetingPage,
    Contact,
  },
  methods: {
    toggleMenu: function () {
      this.menuOpened = !this.menuOpened;
    },
  },
  computed: {
    contact: function () {
      return {
        mainText:
          "<p>Want to get in touch? Awesome! <p/> \
          <p>I am actively looking for new grad opportunities in software development and I'd love to hear from any \
          employers interested in me. Please feel free to reach out using one of the following methods.</p> \
          <p>Preferably email : )<p/>",
        contactItems: [
          {
            logoUrl: "/Static/Icons/gmail.svg",
            linkUrl: "mailto: bgeleto@macalester.edu",
            contactMethod: "bgeleto@macalester.edu",
          },
          {
            logoUrl: "/Static/Icons/github-logo.svg",
            linkUrl: "https://github.com/beckaberhanu",
            contactMethod: "github.com/beckaberhanu",
          },
          {
            logoUrl: "/Static/Icons/linkedin.svg",
            linkUrl: "https://linkedin.com/in/becka-geleto",
            contactMethod: "linkedin.com/in/becka-geleto",
          },
          {
            logoUrl: "/Static/Icons/phone.svg",
            linkUrl: "tel:651-434-0971",
            contactMethod: "(651)-434-0971",
          },
        ],
      };
    },
  },
  data: function () {
    return {
      menuOpened: false,
      greetingPage: {
        WelcomeMessage:
          '<p> This portfolio contains a highlight of some of my experiences as a software developer, computer science student and overall technology enthuthiast. I’ve included my past \
          and present <a href="#project-section">projects</a>, extra curricular <a href="#activities-section">activities</a>, and relevant skills. </p> \
          <p>I am still accepting feedback on this webpage so please don\'t hesitate to <a href="#contact-section">contact me</a> with any questions, tips and suggestions you may have \
          about the content or format of this webpage. </p>',
      },
      aboutMe: {
        mainText:
          '<p>Hello! My name is Becka Geleto. I am asoftware developer from St. Paul, Minnesota. I am currently senior at <a href="https://www.macalester.edu" target="_blank">Macalester College</a> where I have majored in computer science.</p> \
          <p>I am excited to get an opportunity to bridge my education with real world experience that I can learn and grow from.</p>',
        imageUrl: "/Static/Images/{Misc}SanFranciscoBeachPicture[Mid].jpg",
        imageCaption:
          "Picture taken at Baker Beach during a brief break from <b>Twitter</b>’s weeklong <b>#EarlyBird</b> program in <b>San Francisco, CA</b>. Good Times!",
      },
      projects: [
        {
          imageUrl: "/Static/Images/{Project}DeveloperPortfolio[Small].jpg",
          mainTitle: "Portfolio WebSite",
          tags: ["Vue.Js", "Adobe XD", "Github Pages"],
          teamMates: [],
          description:
            "I developed this website using VueJs to showcase my CS projects to employers. The website was designed using Adobe \
            XD and the UI was implemented using a priciple called 'Responsive Web Design' so that it can properly fit a wide variety \
            of devices.",
          externalLinks: [
            {
              url:
                "https://github.com/beckaberhanu/DeveloperPortfolioWebsite-VueJs-2020",
              icon: "/Static/Icons/github-logo.svg",
              name: "Github",
            },
            {
              url: "https://beckaberhanu.github.io",
              icon: "/Static/Icons/monitor.svg",
              name: "Demo",
            },
          ],
        },
        {
          imageUrl: "/Static/Images/{Project}TextBookSwap[Small].jpg",
          mainTitle: "Textbook Swap Website",
          tags: ["Django", "Python", "Adobe XD"],
          teamMates: [
            {
              name: "Nadav Skloot",
              icon: "/Static/Icons/github-logo.svg",
              link: "https://github.com/nadavskloot",
            },
            {
              name: "Tianrui Lui",
              icon: "/Static/Icons/linkedin.svg",
              link: "https://www.linkedin.com/in/tianrui-liu-6443bb149",
            },
            {
              name: "Qingru Zhang",
              icon: "/Static/Icons/linkedin.svg",
              link: "https://www.linkedin.com/in/qingru-zhang/",
            },
          ],
          description:
            "A website for selling, purchasing and swapping textbooks. I developed this website alongside 3 team-mates for a software design and development \
            course that I took during the spring 2020 semester",
          externalLinks: [
            {
              url: "https://github.com/beckaberhanu/TextBookSwap",
              icon: "/Static/Icons/github-logo.svg",
              name: "Github",
            },
          ],
        },
        {
          imageUrl: "/Static/Images/{Project}ManiacalEgg[Small].jpg",
          mainTitle: "Maniacal Egg",
          tags: ["Vue.js", "Python", "Adobe XD"],
          teamMates: [
            {
              name: "Lena Underwood",
              icon: "/Static/Icons/github-logo.svg",
              link: "https://github.com/lenaunderwood22",
            },
            {
              name: "Ryan Kinnucan",
              icon: "/Static/Icons/linkedin.svg",
              link: "https://www.linkedin.com/in/ryankinnucan/",
            },
            {
              name: "Elisabeth Landgren",
              icon: "/Static/Icons/github-logo.svg",
              link: "https://github.com/elishbeth",
            },
          ],
          description:
            "A webapp for filtering through courses offered at Macalester College in a clear and intuitive manner. I developed this web app along with three friends to solve some recurring difficulties we \
            faced while trying to register for courses.",
          externalLinks: [
            {
              url: "https://github.com/beckaberhanu/ManiacalEgg-MyCopy",
              icon: "/Static/Icons/github-logo.svg",
              name: "Github",
            },
            {
              url: "https://beckageleto.dev/ManiacalEgg-MyCopy",
              icon: "/Static/Icons/monitor.svg",
              name: "Github",
            },
          ],
        },
        {
          imageUrl: "/Static/Images/{Project}MachineLearningJava[Small].jpg",
          mainTitle: "[MNIST] Machine Learning Project",
          tags: ["Java", "Machine Learning"],
          teamMates: [],
          description:
            "Built a basic machine learning algorithm from the ground up using Java. Implemented as a multilayer perceptron with multiple \
            configurable parameters such as network architecture, depth, learning rate and bias. <p>Able to make predictions with up to 92% \
            accuracy on the MNIST dataset of 60,000 handwritten digits at its current state.</p>",
          externalLinks: [
            {
              url: "https://github.com/beckaberhanu/MachineLearning2",
              icon: "/Static/Icons/github-logo.svg",
              name: "Github",
            },
          ],
        },
      ],
      workExperience: [
        {
          imageUrl: "/Static/Images/{Experience}LyftDashBoardLight[Small].jpeg",
          mainTitle: "Lyft: Software Engineer Intern",
          tags: ["React", "Node", "Test driven development"],
          teamMates: [],
          description:
            "<p>Migrated an internal web portal used by Lyft’s CET agents to create, upload, and approve or reject driver incentive bonuses to a new technology stack built on the React and Node web frameworks.<p/>\
            <p>	Utilized test driven development to incrementally prototype, test, and deploy features and fixes in a timely manner.<p/>",
          externalLinks: [
          ],
        },
        {
          imageUrl: "/Static/Images/{Experience}SayKidLogoWhiteBG[Small].jpeg",
          mainTitle: "SayKid: Software Development Intern",
          tags: ["WordPress.Org", "PHP", "Web Development"],
          teamMates: [],
          description:
            "<p>Developed an online subscription model for access to SayKid’s voice enabled, play-based learning platform<p/>\
            <p>Redesigned the company’s website to be more responsive, visually appealing and intuitive<p/>",
          externalLinks: [
          ],
        }
      ],
      activities: [
        {
          imageUrl: "/Static/Images/{Activity}MacHackMeeting[Small].jpg",
          mainTitle: "MacHack: Macalester Computer Science Club",
          tags: ["CS", "Student Org", "Weekly Meetings"],
          teamMates: [],
          description:
            "MacHack is a Macalester College student org that hosts events and gatherings for students interested \
            in Computer Science. We have routine weekly meetings where we present on and discuss various \
            computer science topics.",
          externalLinks: [
            {
              url: "mailto: machack@macalester.edu",
              icon: "/Static/Icons/gmail.svg",
              name: "Email",
            },
          ],
        },
        {
          imageUrl:
            "/Static/Images/{Activity}MinnehackGroupPhoto2020Comp[Small].jpg",
          mainTitle: "Minnehack 2020: University of Minnesota Hackathon",
          tags: ["Hackathon", "Team work"],
          teamMates: [],
          description:
            "Minnehack is a yearly hackathon hosted by University of Minnesota Association for Computing \
            Machinery. It was a 24 hour event where participants compete to build the best project on a theme.\
            The theme that year was to develop a solution for 'local communities' to prmotoe 'social good'",
          externalLinks: [
            {
              url: "https://minnehack.io/",
              icon: "/Static/Icons/external-link.svg",
              name: "Minnehack",
            },
          ],
        },
        {
          imageUrl: "/Static/Images/{Activity}EarlyBirdTwitter[Small].jpg",
          mainTitle: "#EarlyBird: Twitter Summer Workshop",
          tags: ["Workshop", "Competition", "2nd place"],
          teamMates: [],
          description:
            "I was selected to participate in a weeklong educational summer program at Twitter's headquarters in \
            San Francisco, California. Collaborated with 4 other participants and a senior software engineer to \
            design, implement and pitch a new feature to a panel of judges. My team was awarded 2<sup>nd</sup> place.",
          externalLinks: [
            {
              url: "https://twitterearlybirdcamp.splashthat.com/",
              icon: "/Static/Icons/external-link.svg",
              name: "#EarlyBird",
            },
          ],
        },
      ],
    };
  },
  mounted: function () {
    document.title = "Becka Geleto";
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Bungee+Inline&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Courier+Prime:ital,wght@0,400;0,700;1,400;1,700&display=swap");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 100%;
  
  overflow-y: scroll;
  scroll-snap-type: y mandatory;
  scroll-snap-stop: always;
  scroll-behavior: smooth;
  max-height: 100vh;
}
html,
body {
  margin: 0;
  height: 100%;
  width: 100%;
}
body {
  background-color: #1b2234;
}
.top-nav-bar {
  background-color: #1b2234;
  box-shadow: 0 3px 5px rgba(0, 0, 0, 0.5);
  position: fixed;
  height: 70px;
  width: 100%;
  transition: top 0.3s;
  z-index: 5;

  display: flex;
  align-items: center;
  justify-content: space-between;
}
.back-to-top {
  text-decoration: none;
}
.back-to-top:hover {
  text-decoration: none;
}
.back-to-top:visited {
  text-decoration: none;
}
.site-logo {
  margin: 0 0 0 30px;
  font-family: "Bungee Inline", cursive;
  font-weight: normal;
  font-size: 2.3em;
  transform: scale(0.9, 1);
  transform-origin: 0 50%;
  justify-self: flex-start;
  min-width: max-content;
  color: #00efab;
}
.nav-sections {
  display: flex;
  justify-self: flex-end;
  margin: 0 30px 0 0;
}
.nav-sections a {
  text-decoration: none;
  color: #00ddee;
  font-size: 0.9em;
  font-weight: 700;
  margin: 0 13px;
  position: relative;
  min-width: max-content;
}
.nav-sections a:visited {
  text-decoration: none;
}
.nav-sections a:hover {
  text-decoration: none;
}
.nav-sections .resume-btn {
  color: #ff4491;
}
.nav-sections a::after {
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
.nav-sections .resume-btn::after {
  background-color: #ff4491;
}
.nav-sections a:hover::after {
  width: 80%;
  left: 10%;
  opacity: 1;
}
.nav-sections a {
  text-decoration: none;
}
.hamburger-button {
  display: none;
  z-index: 10;
  filter: hue-rotate(0deg);
  transition: transform 0.2s, filter 0.3s;
  transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
}
.hamburger-button:active {
  transform: scale(0.9);
  filter: hue-rotate(90deg);
}
.hamburger-button img {
  height: 25px;
  width: 25px;
}
.greeting-section,
.about-me-section {
  scroll-snap-align: start;
  height: 100vh;
  width: 100%;
}
.about-me-section {
  background-color: #1b2234;
  top: 0;
  display: flex;
  position: sticky;
}
.experience-section {
  background-color: #212a40;
}
.project-section {
  background-color: #1b2234;
}
.activities-section {
  background-color: #212a40;
}
.contact-section {
  background-color: #1b2234;
}
.left-side-spacer {
  flex: 2;
  min-width: 13vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.left-side-spacer h1 {
  writing-mode: vertical-rl;
  transform: scale(-1, -1);
  text-orientation: mixed;
  font-family: "Bungee Inline", cursive;
  font-weight: unset;
  font-size: 12vh;
  margin: 0;
  color: #212a40;
}
.left-side-spacer.v1 h1 {
  color: #212a40;
}
.left-side-spacer.v2 h1 {
  color: #1b2234;
}
.right-side-spacer {
  flex: 1;
  min-width: 3%;
}
.stacking-slide {
  scroll-snap-align: start;
  height: 100vh;
  width: 100%;
  position: sticky;
  top: 0;
  box-shadow: 0 -5px 20px rgba(0, 0, 0, 0.5);
  display: flex;
}
.section-content {
  display: flex;
  align-items: center;
  width: 1100px;
  margin: 50px 0;
  z-index: 1;
}
.vertical-text-container {
  max-width: min-content;
  display: contents;
}
.about-webpage {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #131824;
  scroll-snap-align: end;
  position: sticky;
  height: 250px;
  box-shadow: 0 -5px 80px rgba(0, 239, 171, 50%);
}
.about-webpage p {
  font-size: 1em;
  color: #fff;
  margin: 7px 20px;
}
.about-webpage b {
  font-family: "Courier New", Courier, monospace;
  color: #00efab;
}
@media only screen and (max-width: 900px) {
  .left-side-spacer {
    flex: 1;
    min-width: 3%;
  }
  .left-side-spacer h1 {
    display: none;
  }
}
@media only screen and (max-width: 740px) {
  .top-nav-bar {
    height: 50px;
  }
  .site-logo {
    margin: 0 0 0 20px;
    font-size: 1.8em;
  }
  .nav-sections {
    position: fixed;
    z-index: 5;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    top: 0;
    bottom: 0;
    margin: 0;
    padding: 20vh 0px 0px 0px;
    width: 200px;
    right: -40px;
    background-color: #0f1526d0;
    backdrop-filter: blur(2px);
    box-shadow: -10px 0 15px rgba(0, 0, 0, 0.5);
    perspective: 900px;
    perspective-origin: 50% 50%;

    transition: right 0.5s;
    transition-timing-function: cubic-bezier(0.19, 1, 0.22, 1);
  }
  .nav-sections.closed {
    right: -300px;
  }
  .nav-sections a {
    margin: 8% 0 8% -20px;
    font-size: 1.2em;
    padding: 10px 20px;
    background-color: #212a40;
    border-radius: 3px;
    box-shadow: 3px 5px 7px rgba(0, 0, 0, 0.5);
    transition: transform 0.08s;
    transition-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
  }
  .nav-sections a:active {
    transform: translateZ(14px) rotate3d(0, 1, 0, -10deg);
    transform-origin: 50% 0%;
  }
  .hamburger-button {
    display: unset;
    margin-right: 15px;
  }
  .greeting-section,
  .about-me-section {
    scroll-snap-align: unset;
    height: unset;
  }
  .greeting-section {
    height: 100%;
  }
  .about-me-section {
    position: unset;
    top: unset;
  }
  .stacking-slide {
    background-color: #1b2234;
    scroll-snap-align: unset;
    height: unset;
    position: unset;
    top: unset;
    box-shadow: none;
  }
  section {
    min-height: 100%;
  }
  .Org-main-panel .main-tile {
    height: 300px;
  }
  .about-webpage {
    position: unset;
    scroll-snap-align: none;
    box-shadow: none;
  }


}
</style>
