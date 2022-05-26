<template>
  <div id="app">
    <VueSonar
      :radius="radius"
      :background="background"
      :hand="hand"
      :dots="dots"
    />
  </div>
  <div id="controls">
    <h4>Radius</h4>
    <span>Radius: <input type="range" min="50" max="500" step="10" v-model="radius"> {{radius}}</span>
    <h4>Background</h4>
    <span>Color: <input type="color" v-model="background.color"> {{background.color}}</span>
    <span>Pattern: <input type="checkbox" v-model="background.pattern"> {{background.pattern}}</span>
    <span>Pattern Color: <input type="color" v-model="background.patternColor"> {{background.patternColor}}</span>
    <h4>Hand</h4>
    <span>Color: <input type="color" v-model="hand.color"> {{hand.color}}</span>
    <span>Width: <input type="range" min="2" max="10" v-model="hand.width"> {{hand.width}}</span>
    <h4>Sample Dot</h4>
    <p>Here we only show 1 dot but more dots are also possible.</p>
    <span>Radius: <input type="range" min="2" max="10" v-model="dots[0].r"> {{dots[0].r}}</span>
    <span>Color: <input type="color" v-model="dots[0].color"> {{dots[0].color}}</span>
    <p>
      cx: x of the center of the dot. x grows the same as math <br/>
      cy: y of the center of the dot. y grows from top to bottom
    </p>
    <div>
      <span>cx: <input type="range" min="0" :max="radius*2" v-model="dots[0].cx"> {{dots[0].cx}}</span>
      <span>cy: <input type="range" min="0" :max="radius*2" v-model="dots[0].cy"> {{dots[0].cy}}</span>
    </div>
    <span>Blink: <input type="checkbox" v-model="dots[0].blink"> {{dots[0].blink}}</span>
  
  </div>
</template>

<script>
import VueSonar from '@/vue-sonar.vue';
export default {
  name: 'ServeDev',
  components: {
    VueSonar
  },
  data() {
    return {
      radius: 250,
      background: {
        color: 'black',
        pattern: true,
        patternColor: 'green'
      },
      hand: {
        color: 'green',
        width: 4
      },
      dots: [
        {
          cx:50,
          cy:150,
          r:5,
          color:'green',
          blink: true
        },
      ]
    }
  }
};
</script>

<style>
#controls {
  display: flex;
  flex-direction: column;
  font-family: ubuntu;
}
#controls :where(span, h4)  {
  padding: 0.5rem;
}
h4 {
  color: green;
  margin:0
}
p {
  padding: 0 0.5rem;
}
</style>