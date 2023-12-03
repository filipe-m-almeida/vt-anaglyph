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
    <!-- <div>lalaal</div> -->
    <!-- <v-stage :config="configKonva">
      <v-layer :config="layerConfig">
        <v-text :config="textConfig"/>
      </v-layer>
    </v-stage>   -->
    <!-- <TheWelcome /> -->
    <Text/>
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
      layerConfig: {
        x: (window.innerWidth / 2) - (layerWidth / 2),
        y: (window.innerHeight / 2) - (layerHeight / 2)
      },
      textConfig: {
        text: textContent,
        width: layerWidth,
        wrap: 'word',
        align: 'center'
      }
    };
  }
};
</script>

<style scoped>
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
