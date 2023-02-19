Public API (Application Programming Interface) of a component:
1. Input Property: Pass value to the component
2. Output Property: Raise event

# Input property
In this example, we want to pass ```post.isFavorite``` in ```app.component.ts``` which got from server to the favorite component by binding it to ```isFavorite``` parameter in ```favorite.component.ts``` parameter of the component<br>
```
  // File: app.component.ts
  // Suppose this post object we get from the server
  // We will display the icon base on post.isFavorite value
  post = {
    title: "Title",
    isFavorite: false
  }

```
Inside the component, using @Input mark field property as input property which makes it available to bind from outside
```
// file: favorite.component.ts

import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'favorite',
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


In template, we bind field ```isFavorite``` of favorite component to ```post.isFavorite``` which is  got from database
```
<!-- File: app.component.html -->
<favorite [isFavorite]="post.isFavorite"></favorite>
```

Favorite component template
```
<!-- file: favorite.component.html -->
<!-- 
    Render [class.bi-star-fill] whenever isFavorite is true
    Render [class.bi-star]      whenever isFavorite is false
    handle click event
 -->
<i
    class="bi"
    [class.bi-star-fill] = "isFavorite" 
    [class.bi-star] = "!isFavorite"
    (click)="onClick()"
>
</i>

```
# Aliasing Input Property
Benefit: Alias keep contract of component stable
In the code above, the parameter in ```app.component.html``` and ```favorite.component.ts``` must have same name ```isFavorite```.<br>
If we want template parameter has different name such as ```is-favorite```, this name is not allow in js, Aliase get involved <br>

Nothing change in app.component.ts
```
  // File: app.component.ts
  // Suppose this post object we get from the server
  // We will display the icon base on post.isFavorite value
  post = {
    title: "Title",
    isFavorite: false
  }

```

In template, we use alias ```is-favorite``` for the field ```isFavorite``` of favorite component and bind it to ```post.isFavorite``` which is  got from database
```
<!-- File: app.component.html -->
<favorite [is-favorite]="post.isFavorite"></favorite>
```


In ```component.ts``` Passing template parameter to ```@IInput()``` method to make aliase
```
// file: favorite.component.ts
import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'favorite',
  templateUrl: './favorite.component.html',
  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input('is-favorite') isFavorite = false;
  
  constructor() { }
  ngOnInit(): void {
  }
  
  onClick() {
    this.isFavorite = !this.isFavorite;
  }
}

```

Nothing change in Favorite component template
```
<!-- file: favorite.component.html -->
<!-- 
    Render [class.bi-star-fill] whenever isFavorite is true
    Render [class.bi-star]      whenever isFavorite is false
    handle click event
 -->
<i
    class="bi"
    [class.bi-star-fill] = "isFavorite" 
    [class.bi-star] = "!isFavorite"
    (click)="onClick()"
>
</i>

