<template>
  <div class="connect-container">
    <div
      class="connect-card"
      v-show="this.$store.state.cardScreen === 'connect'"
    >
      <div class="back" @click="changeScreen('home')">
        <div class="svg-wrapper">
          <img class="back-arrow" src="@/assets/angles-left-solid.svg" />
        </div>
        <p class="back-text">Back</p>
      </div>
      <div class="title">
        <p class="title-text">C O N N E C T</p>
      </div>
      <div class="vin"></div>
      <div class="highlight"></div>
      <div class="overlay"></div>
      <div class="connect-icon-box">
        <div class="linkedin button" @click="goToLinkedIn()">
          <div class="svg-wrapper">
            <img class="icon" src="@/assets/linkedin-brands.svg" />
          </div>
          <div v-show="connect" class="icon-title">Connect</div>
        </div>

        <div class="twitter button" @click="goToTwitter()">
          <div class="svg-wrapper">
            <img class="icon" src="@/assets/twitter-brands.svg" />
          </div>
        </div>

        <div class="instagram button" @click="goToInstagram()">
          <div class="svg-wrapper">
            <img class="icon" src="@/assets/instagram-brands.svg" />
          </div>
        </div>
        <div class="github button" @click="goToGitHub()">
          <div class="svg-wrapper">
            <img class="icon" src="@/assets/github-brands.svg" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ConnectBlock",
  data() {
    return {};
  },
  methods: {
    changeScreen(screen) {
      this.$store.dispatch(`triggerScreenChange`, screen);
    },
    goToLinkedIn() {
      window.open("https://www.linkedin.com/in/brettyoncak");
    },
    goToTwitter() {
      window.open("https://www.twitter.com/needmorejpegs");
    },
    goToInstagram() {
      window.open("https://www.instagram.com/brettyoncak");
    },
    goToGitHub() {
      window.open("https://www.github.com/byoncak");
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/global-styles/colors.sass";

.vin {
  background: radial-gradient(
    circle,
    rgba(255, 255, 255, 0) 40%,
    rgba(10, 69, 52, 0.8) 120%
  );
  border-radius: 1.6rem;
  width: 30.4rem;
  height: 20.4rem;
  position: absolute;
  align-self: center;
  justify-self: center;
  z-index: 3;
  pointer-events: none;
  mix-blend-mode: multiply;
}

.highlight {
  border-radius: 1.6rem;
  background: linear-gradient(
    16deg,
    rgba(80, 96, 212, 0) 0%,
    rgba(#73d393, 0.8) 64%,
    rgba(142, 102, 213, 0) 100%
  );
  width: 30rem;
  height: 20rem;
  position: absolute;
  align-self: center;
  justify-self: center;
  z-index: 5;
  pointer-events: none;
  mix-blend-mode: soft-light;
}

.overlay {
  border-radius: 1.6rem;
  width: 30rem;
  height: 20rem;
  position: absolute;
  align-self: center;
  justify-self: center;
  background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.32) 50%);
  background-size: 100% 3px, 3px 100%;
  z-index: 5;
  pointer-events: none;
  filter: drop-shadow(12px 12px 16px rgba(#000000, 1));
}

.title {
  display: flex;
  justify-content: center;
  align-content: center;
  grid-area: a / b / a / c;
  color: #73d393;
  font-weight: 800;
}

.connect-card {
  border: 3.2px solid #73d393;
  justify-self: center;
  align-self: center;
  display: grid;
  grid-template-areas:
    "a b c d"
    "e f g h"
    "i j k l"
    "m n o p";

  grid-template-rows: repeat(4, 25%);
  grid-template-columns: repeat(4, 25%);
  border-radius: 1.6rem;
  width: 30rem;
  height: 20rem;
  position: relative;
  z-index: 3;
  background-color: #0e3933;
  filter: drop-shadow(0px 0px 24px rgba(#73d393, 0.32));
}

.connect-icon-box {
  display: flex;
  justify-content: center;
  align-items: center;
  grid-column-start: a;
  grid-column-end: d;
  grid-row-start: e;
  grid-row-end: i;
}

.back {
  display: inline-flex;
  grid-area: a;
  align-items: center;
  padding-left: 16px;
  margin-top: -32px;
  justify-content: flex-start;
  width: auto;
  background-color: transparent;
  color: #73d393;
  cursor: pointer;
}

.back-text {
  align-self: center;
  justify-self: center;
  padding-bottom: 2.3px;
}

.back-arrow {
  widows: 18px;
  height: 18px;
  margin-right: 8px;
}

.title-text {
  font-size: 16px;
}
//ICONS

//Connect

.linkedin {
  padding: 1.6em;
  z-index: 5;
}

.twitter {
  padding: 1.6em;
  z-index: 5;
}

.instagram {
  padding: 1.6em;
  z-index: 5;
}

.github {
  padding: 1.6em;
  z-index: 5;
}

.svg-wrapper {
  filter: drop-shadow(0px 0px 5px rgba(#73d393, 1));
}

img.icon {
  filter: invert(87%) sepia(4%) saturate(4085%) hue-rotate(81deg)
    brightness(91%) contrast(81%);
  animation: glitch 4s infinite;
  z-index: 1;
}

img.back-arrow {
  filter: invert(87%) sepia(4%) saturate(4085%) hue-rotate(81deg)
    brightness(91%) contrast(81%);
  animation: glitch 4s infinite;
  z-index: 1;
}

.connect-container {
  display: flex;
  width: 100vw;
  justify-content: center;
}

.button {
  color: $green;
  font-size: 1em;
  font-weight: lighter;
  margin-top: 0px;
  padding: 32px;
  transition: margin 0.2s ease-in-out;
  background: transparent;
  cursor: pointer;
  z-index: 4;
}
.icon {
  height: 2rem;
  width: auto;
  z-index: 1;
}

.icon-title {
  display: flex;
  color: $green;
  margin-top: 0.4em;
  max-width: 2em;
  justify-content: center;
}
.button:hover {
  margin-top: -24px;
  transition: margin 0.3s ease-in-out;
  cursor: pointer;
}

//animations
@-webkit-keyframes glitch {
  0% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
  }
  5% {
    -moz-transform: skewX(2deg);
    -ms-transform: skewX(2deg);
    -webkit-transform: skewX(2deg);
    transform: skewX(2deg);
    opacity: 0.88;
  }
  10% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
    opacity: 1;
  }
  15% {
    -moz-transform: skewX(-3deg);
    -ms-transform: skewX(-3deg);
    -webkit-transform: skewX(-3deg);
    transform: skewX(-3deg);
    opacity: 0.88;
  }
  20% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
    opacity: 1;
  }
  45% {
    -moz-transform: skewX(3deg);
    -ms-transform: skewX(3deg);
    -webkit-transform: skewX(3deg);
    transform: skewX(3deg);
    opacity: 0.88;
  }
  50% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
    opacity: 1;
  }
  55% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
    opacity: 0.88;
  }
  60% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
    opacity: 1;
  }
  88% {
    -moz-transform: skewX(2deg);
    -ms-transform: skewX(2deg);
    -webkit-transform: skewX(2deg);
    transform: skewX(2deg);
  }
  80% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
  }
  85% {
    -moz-transform: skewX(-4deg);
    -ms-transform: skewX(-4deg);
    -webkit-transform: skewX(-4deg);
    transform: skewX(-4deg);
    opacity: 0.88;
  }
  90% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
    opacity: 1;
  }
  100% {
    -moz-transform: skewX(0deg);
    -ms-transform: skewX(0deg);
    -webkit-transform: skewX(0deg);
    transform: skewX(0deg);
  }
}
</style>
