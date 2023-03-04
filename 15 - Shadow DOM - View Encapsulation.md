Shadow DOM allows us to apply scoped styles to elements without bleeding out the outer world<br>
# Javascript Example
```
el.innerHTML = `
  <style> h1 { color: red } </style>
  <h1>Hello</h1>
`;
```

This style is leak. Not only the h1 we want to set red but also all h1 get red.<br>
We want the style only value in its scope which is its component. Shadow DOM is used.
```
var el = document.querySelector('favorite');
var root = el.createShadowRoot();
root.innerHTML = `
  <style> h1 { color: red } </style>
  <h1>Hello</h1>
`;
```
# Angular
Add ```encapsulation: ViewEncapsulation.ShadowDom,``` property to director
```
// file: Favorite.component.ts
import { Component, OnInit, Input, Output, EventEmitter, ViewEncapsulation } from '@angular/core';

@Component({
  selector: 'favorite-component',
  templateUrl: './favorite.component.html',
  styles: [
     `
      .bi {
        color: green;
      }
     `
  ],
  styleUrls: ['./favorite.component.css'],
  encapsulation: ViewEncapsulation.ShadowDom,
})
export class FavoriteComponent {

  @Input('is-favorite') isSelected = false;
  @Output('change') click = new EventEmitter();
  constructor() { }

  onClick() {
    this.isSelected = !this.isSelected;

    // Pass an object
    this.click.emit({ newValue: this.isSelected });
  }
}

export interface FavoriteChangedEventArgs {
  newValue: boolean
}
```

The star will disappear because all style of this component is encapsulated. This block bootstrap style shows up. To show the star up, add bootstrap to favorite.component.css
```
/* file: favorite.component.css */

@import "~bootstrap-icons/font/bootstrap-icons.css";

.bi {
    color: red;
    background-color: yellow;
}
```
