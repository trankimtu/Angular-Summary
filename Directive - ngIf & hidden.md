# Directive - ngIf
We use directive to modify the DOM<br>
There's 2 type of directives:
1. Structure directive: Modify the structure of the DOM
2. Attribute directive: Modify the attributes of DOM elements.
<br>

# ngIf
In this example, we will modify the structure of the DOM by adding or removing one DOM element.<br>
Benefit: If we are not going to show large element trees, ```ngIf``` will take it out of the DOM. This will save resource
Use ```*``` for structure directive<br>
We will show or hide part of a page depending on some conditions:<br>
1. Courses array empty will show “No courses yet”<br>
2. Courses array not empty will show “List of courses”


```
// File: app.component.ts

import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  courses = [];
}
```

Condition ```courses.length > 0``` can be a boolean method<br>
```#``` is used to define template variable
```
<!-- app.component.html -->

<div *ngIf="courses.length > 0; then coursesList else noCourse"></div>

<ng-template #coursesList>
  List of courses
</ng-template>

<ng-template #noCourse>
  No courses yet
</ng-template>
```

# Hidden
Use hidden property to hide a ```div```. When add ```hidden``` property to the ```div```, that ```div``` is hidden <br>
The code bellow only show "No courses yet"
```
<div hidden>
  List of courses
</div>

<div>
  No courses yet
</div>
```

Using hidden, both div is exist in the DOM. This takes resource
Benefit for small element tree or hidden ```div``` which is show up when raise event.

```
// File: app.component.ts

import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  courses = [];
}
```
Bind hidden property to an expression
```
<!-- File: app.component.html -->
<div [hidden]="courses.length == 0">
  List of courses
</div>

<div [hidden]="courses.length > 0">
  No courses yet
</div>

```
