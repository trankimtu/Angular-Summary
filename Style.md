# Style in Angular
3 ways to apply styles for a component<br>
## 1st way: Use the stileUrls
```
/* file: favorite.component.css */
.bi {
    color: red;
    background-color: yellow;
}
```
## 2nd way: in decorator
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
## 3rd way: inline html template
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
Style in favorite.component.html will 1st priority<br>
In the clip, which one come last on favorite.component.ts will be 2nd priority. Angular pick one style and ignore whatever in other style<br>
My case, style in favorite.component.ts is 2nd priority doesn’t matter it come before or after styleUrls. Angular match all the style together. The same style will be overwrited by other.
