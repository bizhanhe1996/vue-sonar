<template>
  <svg :width="size" :height="size" :viewBox="`0 0 ${size} ${size}`" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <!-- Definitions -->
      <pattern id="pattern" viewBox="0,0,48,48" width="10%" height="10%">
        <g :fill="background.patternColor">
          <path opacity='.5' d='M96 95h4v1h-4v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4h-9v4h-1v-4H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15v-9H0v-1h15V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h9V0h1v15h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9h4v1h-4v9zm-1 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm9-10v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-10 0v-9h-9v9h9zm-9-10h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9zm10 0h9v-9h-9v9z' />
          <path d='M6 5V0H5v5H0v1h5v94h1V6h94V5H6z'/>
        </g>
      </pattern>
    </defs>
    <!-- Circle with Background Color -->
    <circle :cx="cx" :cy="cx" :r="cx" :fill="background.color"/>
    <!-- Circle With Background Pattern -->
    <circle :cx="cx" :cy="cx" :r="cx" :style="{'fill':background.pattern?'url(#pattern)':'none'}" />
    <!-- Hand -->
    <line :x1="cx" :y1="cx" :x2="size-1" :y2="cx" :stroke="hand.color" :stroke-width="hand.width" />
    <!-- Center Circle -->
    <circle :cx="cx" :cy="cx" :r="size/50" fill="green" />
    <!-- Dots -->
    <circle v-for="(dot, index) in dots" :key="index"  :cx="dot.cx" :cy="dot.cy" :r="dot.r" :fill="dot.color">
      <animate attributeName="fill-opacity" dur="2s" repeatCount="indefinite" values="0;1;0;" v-if="dot.blink" />
    </circle>
  </svg>
</template>

<script>
export default {
  name:'VueSonar',
  props: {
    radius: Number,
    background: Object,
    hand: Object,
    dots: Array,
  },
  computed: {
    cx() {
      return this.size / 2;
    },
    size() {
      return this.radius * 2;
    }
  }
}
</script>

<style scoped>
@-webkit-keyframes sonar {
  0% {
    -webkit-transform: rotate(0deg);
      transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}

@keyframes sonar {
  0% {
    -webkit-transform: rotate(0deg);
      transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
      transform: rotate(360deg);
  }
}

line {
  -webkit-transform-origin: center;
    transform-origin: center;
  -webkit-animation-name: sonar;
    animation-name: sonar;
  -webkit-animation-duration: 4s;
    animation-duration: 4s;
  -webkit-animation-iteration-count: infinite;
    animation-iteration-count: infinite;
  -webkit-animation-timing-function: linear;
    animation-timing-function: linear;
  stroke-linecap: round;
}
</style>