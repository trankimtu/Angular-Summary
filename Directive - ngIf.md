# Directive - ngIf
We use directive to modify the DOM<br>
There's 2 type of directives:
1. Structure directive: Modify the structure of the DOM
2. Attribute directive: Modify the attributes of DOM elements.
<br>
In this example, we will show or hide part of a page depending on some conditions
1. Courses array empty will show “No courses yet”
2. Courses array not empty will show “List of courses”


# app.component.ts
```
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

# app.component.html
```
<div *ngIf="courses.length > 0; then coursesList else noCourse"></div>

<ng-template #coursesList>
  List of courses
</ng-template>

<ng-template #noCourse>
  No courses yet
</ng-template>
```
