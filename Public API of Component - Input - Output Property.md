Public API (Application Programming Interface) of a component:
1. Input Property: Pass value to the component
2. Output Property: Raise event

# Input property
In this example, we want to pass ```post.isFavorite``` in ```app.component.ts``` which got from server to the favorite component by binding it to ```isFavorite``` parameter in ```favorite.component.ts``` parameter of the component
Then use @Input mark field property as input property and make the field available to bind from outside
```
// file: favorite.component.ts

import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'angular-favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input() isFavorite = false;
  
  constructor() { }
  ngOnInit(): void {
  }
  
  onClick() {
    this.isFavorite = !this.isFavorite;
  }
}
```
