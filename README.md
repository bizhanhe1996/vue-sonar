<p style="text-align:center">
    <img width="250" height="250" src="https://github.com/bizhanhe1996/vue-sonar/blob/master/demo.gif?raw=true" />
</p>

# vue-sonar
An animated responsive sonar made by SVG for Vue 3

## Demo
A demo of the package is available <a href="https://c2b8qy.csb.app/" target="_blank">HERE</a>

## Getting Started
1. Install it using NPM
```
npm i vue-sonar
```
2. Import it into your vue file
```
import VueSonar from 'vue-sonar';
```
3. Register it (globally or locally)
```
components: {
    VueSonar
}
```
4. Add it to your template with its parameters (Could be bound)
```
<VueSonar 
    :radius="radius"
    :background="background"
    :hand="hand"
    :dots="dots"
/>
```

## Parameters
| Name | Type | Map | Description |
| ---- | ---- | ----------- | ---- |
| radius | Integer | | the radius of the sonar board |
| background | Object | {<br/>color: String<br/>pattern: Boolean<br/>patternColor: String<br/>} | some properties about the style of the background of sonar board |
| hand | Object | {<br/>color: String<br/>width: Integer<br/>} | some properties about the style of the hand of sonar |
| dots | Array of Objects | {<br/>cx: Integer,<br/>cy: Integer<br/>r: Integer<br/>color: String<br/>blink: Boolean<br/>} | each object inside this array stands for a dot in rader board.<ul> <li>cx: x of the center of the dot, it grows the same as Descartian chart in math</li><li>cy: y of the center of the dot, it grows from top to bottom unlike Descartian chart in math</li><li>r: the radius of the dot</li><li>color: the background color of the dot</li><li>blink: whether the dot should blink or not</li></ul> |