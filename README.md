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
