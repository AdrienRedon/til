# til
📝 Today I Learned

## 07/01/2018

### CSS grid: fit-content

The fit-content property can be used in order to allow smaller reserved space than the column track.

#### How to use
```css
grid-template-columns: fit-content(250px) 1fr;
```
#### codepen: 
https://codepen.io/rachelandrew/pen/KZyaBj

#### Learned from:
[Rachel Andrew](https://twitter.com/rachelandrew/status/950021988453634048)

## 08/01/2018

### Angular: trackBy

```trackBy``` modifies the behavior so that it compares new data to old based on the return value of the supplied trackBy method.
This allows Angular to reduce the amount of DOM update needed.

#### How to use
```html
<!-- instructor-list.component.html.html -->
<ul>
  <li *ngFor="let instructor of instructorList: trackBy: trackByName" >
    <span>Instructor Name {{ instructor.name }}</span>
  </li>
</ul>
```
```typescript
/* instructor-list.component.ts */
import { Component } from '@angular/core';

import { ListService } from '../list.service';

@Component({
  selector: 'app-instructor-list',
  templateUrl: './instructor-list.component.html'
})
export class InstructorListComponent {
  instructorList = {name: string}[];

  constructor(private ls: ListService){
    // In this example let's assume the list service provides the
    // instructors as a realtime list of filtered instructors.
    // New updates are sent at regular intervals regardless of content change.
    // As a result the object references change with each update.
    ls.getList()
      .subscribe(list => this.instructorList = list);
  } 
  
  trackByName(index, instructor) {
    return instructor.name;
  }
}

```
#### Learned from:
[Angular Blog](https://blog.angular.io/3-tips-for-angular-runtime-performance-from-the-real-world-d467fbc8f66e)

## 09/01/2018

### Vue: render single slot component

 You can use render functions instead of templates for single slot components to avoid the extra wrapper element
 
#### How to use
```javascript
Vue.component('element-query', {
  // use a render function to grab the slot directly!
  render() {
    return this.$scopedSlots.default({
      width: this.width,
      height: this.height,
    })
  },
  data() {
    return {
      width: null,
      height: null,
    }
  },
  mounted(){
    erd.listenTo(this.$el, (el) => {
      this.width = el.offsetWidth;
      this.height = el.offsetHeight;
    })
  },
})
```
#### Learned from:
[Adam Wathan](https://twitter.com/adamwathan/status/950782785467199489)

## 10/01/2018

### ES6: Array.from map function

You can provide a second argument to `Array.from` that is a `map` function.

#### How to use
```javascript
Array.from(Array(20), (item, index) => index + 1);
```
#### Learned from:
[Merrick Christensen](https://twitter.com/iammerrick/status/950841613651193858)

## 11/01/2018

### Jasmine: mockDate

It is possible to mock the current date with the ```mockDate``` function of Jasmine.

#### How to use
```javascript
// with native Date
const today = new Date('2015-10-19');
jasmine.clock().mockDate(today);

// with moment.js
const today = moment('2015-10-19').toDate();
jasmine.clock().mockDate(today);
```
#### Learned from:
[jacwah](https://stackoverflow.com/a/33380312)

## 13/01/2018

### DevTools: coverage

Press [ctrl] + [shift] + p or [cmd] + [shift] + p then type code "show coverage". You can then reload the page to see how much code is being unused on the page.

#### Learned from:
[Sean Larkin](https://twitter.com/TheLarkInn/status/952272042786570240)

## 15/01/2018

### ES6: unique array

It is possible to get unique values from an array with Set() and the rest operator.

#### How to use
```javascript
const uniqueArray = (arr) => [...new Set(arr)];
```
#### Learned from:
[Addy Osmani](https://twitter.com/addyosmani/status/952805052086824960)

### Command Line: curly brackets

Use curly brackets in the command line to cut down on typing the same thing over and over

#### How tu use
```shell
$ touch component.{ts,css,html}
```
#### Learned from:
[Wes Bos](https://twitter.com/wesbos/status/952984066093182976)

## 20/01/2018

### Angular: Pure pipe

With Pure pipe, we can optimize expression re-evaluation and get the caching that Angular provides.

#### How to use
```javascript
@Pipe({
  name: 'purePipe',
  pure: true,
})
export class PurePipe {
  transform(input: string, param: string) {
    return input + param;
  }
}
```
#### Learned from:
[Minko Gechev](http://blog.mgechev.com/2017/11/12/faster-angular-applications-pure-pipes-memoization-pure-functions-part-2/)

## 22/01/2018

### CSS: mix-blend-mode

The mix-blend-mode CSS property describes how an element's content should blend with the content of the element's direct parent and the element's background. For instance we can set a text to white and the mix-blend-mode property to difference. That would result in the text being always readable no matter the background.

#### How to use
```css
.readable-text {
  color: white;
  mix-blend-mode: difference;
}
```
#### Learned from:
[Timothy Achumba](https://twitter.com/timothyachumba/status/955364205313568768)

## 23/01/2018

### CSS: Aspect Ratio

It is possible to have a DOM element keep a fixed aspect ratio with a combination of CSS grid and SVG.

#### How to use
```html
<style>
.aspectRatioSizer {
  display: grid;
}
.aspectRatioSizer > * {
  grid-area: 1 / 1 / 2 / 2;
}
</style>
<div class="aspectRatioSizer">
  <svg viewBox="0 0 7 2"></svg>
  <div>
    Content goes here
  </div>
</div>
```
#### codepen:
https://codepen.io/noamr/pen/mpamVN
#### Learned from:
[Noam Rosenthal](https://codeburst.io/keeping-aspect-ratio-with-html-and-no-padding-tricks-40705656808b)

### HTML: preconnect

We can add preconnect hints for any hosts that you will be requesting assets from so the browser can then prep things by establishing all the necessary connections for those resources.

#### How to use
```html
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```
#### Learned from:
[Jeremy Frank](https://www.viget.com/articles/make-your-site-faster-with-preconnect-hints/)

## 30/01/2018

### npm: use specific version of node for project

You can use a specific version of node so any time you do `npm test` or `npm start`, it will use this one, regardless of what your global node version is.

#### How to use
```shell
$ npm install node@7
```
#### Learned from:
[Kat Marchán](https://twitter.com/maybekatz/status/958157474397171712)

## 06/02/2018

### ES6: tagged template strings

You can use tagged template strings to get many editors to syntax-highlight the strings

#### How to use
```javascript
const html = String.raw;
const wired = html`
  <div class="wow">
    html, yay
  </div>
`;
```
#### Learned from:
[Alex Dytrych](https://twitter.com/SomeHats/status/960138211350728704)

## 22/02/2018

### JS: Locale Curency

You can use toLocaleString to format currency

#### How to use
```javascript
100.42.toLocaleString('fr-FR', { style: 'currency', currency: 'EUR' });
// "100,42 €"
100.42.toLocaleString('en-US', { style: 'currency', currency: 'USD' });
// "$100.42"
```
#### Learned from:
[Wes Bos](https://twitter.com/wesbos/status/966697179904651264)

## 27/02/208

### git: changelog

You can use git log to generate a changelog since a given tag.

#### How to use
```shell
$ git log --oneline --no-merges [last tag]..

$ git log --oneline --no-merges v1.10.0..
```
#### Learned from:
[Harry Roberts](https://twitter.com/csswizardry/status/865919323528990720)

## 05/03/2018

### CSS: content-based sizing

You can make your layout fast and static by default by turning on content-based sizing on a per-element basis.

#### How to use
```css
* {
  box-sizing: border-box;
  contain: strict;
}
[autosize] {
  contain: layout style paint;
}
```
#### Learned from:
[Jason Miller](https://twitter.com/_developit/status/970425737512673280)

## 30/12/2018

### JS: addEventListener() once

addEventListener() supports an `once` option.

#### How to use
```javascript
target.addEventListener('click', () => console.log('once'), { once: true })
```
#### Learned from:
[Surma](https://twitter.com/DasSurma/status/1078375282183151617)

## 24/02/2019

### SVG: rotate shape fill-box

To rotate a shape witout using the center of the SVG canvas as the origin of the rotation but its own center, you can add transform-box: fill-box to the shape you're rotating. 

#### How to use
```css
.triangle {
    animation-name: rotation;
    animation-duration: 1s;
    transform-origin: center;
    transform-box: fill-box;
}
@keyframes rotate {
    from { transform: rotate(90deg); }
    to { transform: rotate(0deg); }
}
```
#### Learned from:
[Cassie Evans](https://twitter.com/cassiecodes/status/1099343911632412677)
