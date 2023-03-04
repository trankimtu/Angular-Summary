# Style binding
```
import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
    <button [style.backgroundColor]="isActive ? 'blue' : 'lightblue'">Save</button>
  `
})

export class CoursesComponent {
  isActive = true;
}
```



```
// File: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  canSave = true;
}
```

```
<!-- File: app.component.html -->
<button
  [style.backgroundColor]="canSave ? 'blue' : 'gray'"
  [style.color]="canSave ? 'white' : 'black'"
  [style.fontWeight]="canSave ? 'bold' : 'normal'"
>
  save
</button>
```
# ngStyle
Normally we encapsulate style in css file. Some situations need inline css, we can use this.
Jason with ```key``` represent css style, ```value``` is value
```
<!-- File: app.component.html -->
<button
  [ngStyle]="{
    'backgroundColor': canSave ? 'blue' : 'gray',
    'color' : canSave ? 'white' : 'black',
    'style' : canSave ? 'bold' : 'normal'
  }"
>
  save
</button>
```

# Style in Angular
3 ways to apply styles for a component<br>
## 1st way: Use the styleUrls
```
/* file: favorite.component.css */
.bi {
    color: red;
    background-color: yellow;
}
```
## 2nd way: Use style properties in decorator
```
// file: Favorite.component.ts
import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css'],
  styles: [
     `
     h1 {
       color: green;
       background-color: blue;
     }
     `
  ]
})
```
## 3rd way: html template
```
/* file: favorite.component.html */
<style>
  .bi {
    color: red;
    background-color: yellow;
  }
</style>

<i
    class="bi"
    [class.bi-star-fill] = "isFavorite" 
    [class.bi-star] = "!isFavorite"
    (click)="onClick()"
>
</i>

```

## Style application order
Style in ```favorite.component.html``` will 1st priority<br>
In the clip, which one come last on ```favorite.component.ts``` will be 2nd priority.<br>
Angular pick one style and ignore whatever in other style<br>
My case, style in ```favorite.component.ts``` is 2nd priority doesn’t matter it come before or after styleUrls. Angular match all the style together. The same style will be overwrited by other.
