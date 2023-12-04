<script setup lang="ts">
import Text from './components/Text.vue'
</script>

<template>
  <header>
    <!-- <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" /> -->

    <!-- <div class="wrapper">
      <HelloWorld msg="You did it!" /> -->
    <!-- </div> -->
  </header>

  <main>
    <v-stage :config="configKonva">
      <v-layer>
        <Text :offset="offset" :color="'rgb(255,0,0)'"/>
        <Text :offset="-offset" :color="'rgb(0, 0, 255)'"/>
      </v-layer>
    </v-stage>
  </main>
</template>

<script lang="ts">
import textContent from './main.txt?raw';

var layerWidth = 600;
var layerHeight = 600;

export default {
  data() {
    return {
      configKonva: {
        width: window.innerWidth,
        height: window.innerHeight
      },
      offset: 0
    };
  },
  methods: {
    createKeydownHandler() {
          return (e) => {
            const map = {
              'd': () => this.adjustOffset(1),
              'a': () => this.adjustOffset(-1),
              // 'w': () => this.adjustStrokeWidth(1),
              // 's': () => this.adjustStrokeWidth(-1),
              // 'ArrowLeft': () => this.moveGroups(-10, 0),
              // 'ArrowRight': () => this.moveGroups(10, 0),
              // 'ArrowUp': () => this.moveGroups(0, -10),
              // 'ArrowDown': () => this.moveGroups(0, 10),
              // '2': () => this.adjustSaturation(10),
              // '1': () => this.adjustSaturation(-10),
              // 'Escape': () => this.endDrag(),
              // 'm': () => this.debugVisible = !this.debugVisible,
              ' ': () => this.invertOffset(),
              // '?': () => this.keyHelpVisible = !this.keyHelpVisible,
              // '/': () => {
              //   // TODO: Turn this into a property.
              //   this.$refs.commandPrompt.commandPromptVisible = true;
              //   this.$nextTick(() => {
              //     if (this.$refs.commandPrompt.$refs.commandInput) {
              //       this.$refs.commandPrompt.$refs.commandInput.focus();
              //     }
              //   });
              //   e.preventDefault();
              // },
            };
          const action = map[e.key];
          if (action) {
            action();
          }
        }
      },
      adjustOffset(increment : number) {
        console.log(this.offset);
        this.offset += (increment * 2) * 2;
      },
      invertOffset() {
        this.offset = -this.offset;
      },
    },
    created() {
      this.keydownHandler = this.createKeydownHandler();
      window.addEventListener('keydown', this.keydownHandler);
    },
    beforeDestroy() {
      window.removeEventListener('keydown', this.keydownHandler);
    },

};
</script>

<style>
body {
  background-color: black;
  overflow: hidden;
  fill: white;
}
/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
