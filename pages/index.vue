<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <div class="text-xs-center">
        <Canvas />
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import Canvas from "~/components/Canvas.vue";

export default {
  components: {
    Canvas
  }
};
</script>
