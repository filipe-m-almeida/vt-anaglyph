<template>
      <!-- <v-layer :config="layerConfig"> -->
        <v-text :config="textConfig"/>
      <!-- </v-layer> -->
</template>

<script lang="ts">
import textContent from './../main.txt?raw';

var layerWidth = 600;
var layerHeight = 600;

export default {
  props: {
    offset: {
      type: Number,
      default: 0
    },
    color: {
      type: String,
      default: 'white'
    }
  },
  computed: {
    layerConfig() {
      return {
        x: (window.innerWidth / 2) - (layerWidth / 2) + this.offset,
        y: (window.innerHeight / 2) - (layerHeight / 2),
        // globalCompositeOperation: 'lighter'
      }
      // opacity: 1
    },
    textConfig() {
      return {
        x: (window.innerWidth / 2) - (layerWidth / 2) + this.offset,
        y: (window.innerHeight / 2) - (layerHeight / 2),
        text: textContent,
        width: layerWidth,
        wrap: 'word',
        align: 'left',
        fill: this.color,
        globalCompositeOperation: 'lighter',
        fontSize: 16
      }
    }
  }
};
</script>
