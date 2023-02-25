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
Set event ```change``` = ```new EventEmitter()```<br>
```
// file: favorite.component.ts

import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input(is-favorite) isFavorite = false;
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


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->


# Pass event data while raising an event
In this example, we raise an event ```change``` and pass a boolean parameter to it

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

  onFavoriteChanged(isFavorite) {
    console.log("Favorite Changed: ", isFavorite);
  }
}
```
<!-- =========================================================================================== -->
Inside the component, pass ```this.isFavorite``` to emit in ```onClick()``` method
```
// file: favorite.component.ts

import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input(is-favorite) isFavorite = false;
  @Output() change = new EventEmitter();
  constructor() { }
  ngOnInit(): void {
  }
  
  onClick() {
    this.isFavorite = !this.isFavorite;
    this.change.emit(this.isFavorite);
  }
}
```
<!-- =========================================================================================== -->
In template we pass ```$evnet``` to ```onFavoriteChanged()``` method
```
<!-- File: app.component.html -->
<favorite [is-favorite]="post.isFavorite" (change)="onFavoriteChanged($event)"></favorite>
```


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->


# Passsing an object to a raising event
In this example, we raise an event ```change``` and pass an object to it

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

  onFavoriteChanged(eventArgs:{newValue: boolean}) {
    console.log("Favorite Changed: ", eventArgs.newValue);
  }
}
```
<!-- =========================================================================================== -->
Inside the component, pass an object ```{ newValue: this.isFavorite }``` to emit in ```onClick()``` method
```
// file: favorite.component.ts

import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input(is-favorite) isFavorite = false;
  @Output() change = new EventEmitter();
  constructor() { }
  ngOnInit(): void {
  }
  
  onClick() {
    this.isFavorite = !this.isFavorite;
    this.change.emit( { newValue: this.isFavorite } );
  }
}
```
<!-- =========================================================================================== -->
In template we pass ```$evnet``` to ```onFavoriteChanged()``` method
```
<!-- File: app.component.html -->
<favorite [is-favorite]="post.isFavorite" (change)="onFavoriteChanged($event)"></favorite>
```


<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

# Passsing an object to a raising event - Better the code buy using interface
In this example, we raise an event ```change``` and pass an object to it

We better keep the interface declaring object in ```favorite.component.ts``` and use it in ```app.component.ts```.

```
// File: app.component.ts
import { Component } from '@angular/core';
import { FavoriteChangedEventArgs } from './favorite/favorite.component';

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

  onFavoriteChanged(eventArgs:FavoriteChangedEventArgs) {
    console.log("Favorite Changed: ", eventArgs.newValue);
  }
} 

```
<!-- =========================================================================================== -->
Inside the component, pass an object ```{ newValue: this.isFavorite }``` to emit in ```onClick()``` method
Export the interface to use in ```app.component.ts```
```
// file: favorite.component.ts

import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input(is-favorite) isFavorite = false;
  @Output() change = new EventEmitter();
  constructor() { }
  ngOnInit(): void {
  }
  
  onClick() {
    this.isFavorite = !this.isFavorite;
    this.change.emit( { newValue: this.isFavorite } );
  }
}

export interface FavoriteChangedEventArgs {
  newValue: boolean
}
```
<!-- =========================================================================================== -->
In template we pass ```$evnet``` to ```onFavoriteChanged()``` method
```
<!-- File: app.component.html -->
<favorite [is-favorite]="post.isFavorite" (change)="onFavoriteChanged($event)"></favorite>
```

<!-- =========================================================================================== -->
<!-- =========================================================================================== -->
<!-- =========================================================================================== -->

# Aliasing Output Properties
Benefit: Alias keep contract of component stable<br>
In ```favorite.component.ts``` suppose we change output event name to ```click```, adding parameter ```'change'``` to ```Output()``` to make an output alias
```
// file: Favorite.component.ts
import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input('is-favorite') isSelected = false;
  @Output('change') click = new EventEmitter();
  constructor() { }
  ngOnInit(): void {
  }
  
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

