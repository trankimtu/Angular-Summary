# Directive - ngIf
We use directive to modify the DOM<br>
There's 2 type of directives:
1. Structure directive: Modify the structure of the DOM
2. Attribute directive: Modify the attributes of DOM elements.
<br>
In this example, we will modify the structure of the DOM by adding or removing one DOM element.<br>
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
