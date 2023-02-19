Public API (Application Programming Interface) of a component:
1. Input Property: Pass value to the component
2. Output Property: Raise event

# Output Properties
In this example, we want to raise an event ```change``` which call ```onFavoriteChanged()``` when favorite star is clicked 

```
// File: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  post = {
    title: "Title",
    isFavorite: false
  }

  onFavoriteChanged() {
    console.log("Favorite Changed");
  }
}
```
Inside the component, using @Output to raise event<br>
import ```output``` and ```Eventemitter```<br>
Set event ```change`` = ```new EventEmitter()```<br>
```
// file: favorite.component.ts

import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input() isFavorite = false;
  @Output() change = new EventEmitter();
  constructor() { }
  ngOnInit(): void {
  }
  
  onClick() {
    this.isFavorite = !this.isFavorite;
    this.change.emit();
  }
}
```

In template we add event ```change``` and method ```onFavoriteChanged()``` to the ```favorite`` component call
```
<!-- File: app.component.html -->
<favorite [is-favorite]="post.isFavorite" (change)="onFavoriteChanged()"></favorite>
```
# Pass event data while raising an event

