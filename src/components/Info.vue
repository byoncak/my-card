<template>
  <div class="info-container">
    <div class="info-card" v-show="this.$store.state.cardScreen === 'info'">
      <div class="back" @click="changeScreen('home')">
        <div class="svg-wrapper">
          <img class="back-arrow" src="@/assets/angles-left-solid.svg" />
        </div>
        <p class="back-text">Back</p>
      </div>
      <div class="title">
        <p class="title-text">M Y &nbsp;&nbsp; I N F O</p>
      </div>
      <div class="vin"></div>
      <div class="highlight"></div>
      <div class="overlay"></div>
      <div class="info-collection">
        <div class="info-lines" v-for="info in information" :key="info.id">
          <div class="line">
            <div class="label">
              {{ info.label }}
              <p class="label-text">{{ info.info }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "InfoBlock",
  data() {
    return {
      opacity: 0,
      myResume: {
        icon: "",
        link: "",
      },
      information: [
        {
          id: 0,
          label: "Name: ",
          info: "Brett Yoncak",
        },
        {
          id: 1,
          label: "Email: ",
          info: "brett@bct.studio",
        },
        {
          id: 2,
          label: "Phone: ",
          info: "+1 609-634-8787",
        },
        {
          id: 3,
          label: "Pronouns: ",
          info: "he / him",
        },
      ],
    };
  },
  methods: {
    changeScreen(screen) {
      this.$store.dispatch(`triggerScreenChange`, screen);
    },
    goToResume(link) {
      window.open(link);
    },
    fadeOut() {
      this.opacity = 0;
    },
    fadeIn() {
      this.opacity = 1;
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
  max-width: 80vw;
  width: 30.4rem;
  height: 20.4rem;
  position: absolute;
  align-self: center;
  justify-self: center;
  z-index: 3;
  pointer-events: none;
  mix-blend-mode: multiply;
}

.animate {
  transition: all 1s;
}

.highlight {
  border-radius: 1.6rem;
  background: linear-gradient(
    16deg,
    rgba(80, 96, 212, 0) 0%,
    rgba(#73d393, 0.8) 64%,
    rgba(142, 102, 213, 0) 100%
  );
  max-width: 80vw;
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
  max-width: 80vw;
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
  font-weight: 800;
}

.info-card {
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
  max-width: 80vw;
  height: 20rem;
  position: relative;
  z-index: 3;
  background-color: #0e3933;
  filter: drop-shadow(0px 0px 24px rgba(#73d393, 0.32));
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

.label {
  display: inline-flex;
  font-weight: 900;
  align-items: center;
  justify-content: center;
}

.label-text {
  font-weight: 200;
  padding-left: 1em;
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

.info-collection {
  display: flex;
  flex-direction: column;
  margin-left: 10.4rem;
  margin-right: 2rem;
  justify-content: center;
  margin-top: -3rem;
  align-items: flex-start;
  grid-area: e / a / p / d;
  font-size: 14px;
  color: #73d393;
}

.title-text {
  color: #73d393;
  font-size: 16px;
}

//ICONS

//Skills

.svg-wrapper {
  filter: drop-shadow(0px 0px 5px rgba(#73d393, 1));
}

img.preview {
  filter: sepia(4%) brightness(91%) contrast(81%);
  height: 84px;
  width: 160px;
  z-index: 1;
  object-fit: cover;
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

.info-container {
  display: flex;
  width: 100vw;
  justify-content: center;
}

.button {
  color: $green;
  font-size: 1em;
  font-weight: lighter;
  margin-top: 0px;
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

@-webkit-keyframes fade-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@-webkit-keyframes fade-out {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

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
