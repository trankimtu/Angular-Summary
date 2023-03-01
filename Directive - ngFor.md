# 1. Display Array Value with Index
Export value index of the array to alias local valuable i 
## File: app.component.ts
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  courses = [
    { id: 1, name: 'course1'},
    { id: 2, name: 'course2'},
    { id: 3, name: 'course3'},
  ];
}
```
## File: app.component.html 
```
<ul>
  <li *ngFor="let course of courses; index as i">
    {{ i }} - {{ course.name }}
  </li>
</ul>
```
## Beside index, there are many other value we can export
Visit angular.io, search for “ngForOf”. Select “D(Directive) NgForOf”<br>
[https://angular.io/api/common/NgForOf](https://angular.io/api/common/NgForOf)<br>
•	index: number: The index of the current item in the iterable.<br>
•	count: number: The length of the iterable.<br>
•	first: boolean: True when the item is the first item in the iterable.<br>
•	last: boolean: True when the item is the last item in the iterable.<br>
•	even: boolean: True when the item has an even index in the iterable.<br>
•	odd: boolean: True when the item has an odd index in the iterable.<br>
```
// File: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  courses = [
    { id: 1, name: 'course1'},
    { id: 2, name: 'course2'},
    { id: 3, name: 'course3'},
  ];
}
```
Instead of out put string ```(EVEN)``` we can set style for it
```
<!-- File: app.component.html  -->
<ul>
  <li *ngFor="let course of courses; index as i">
    {{ i }} - {{ course.name }}
  </li>
</ul>

<ul>
  <li *ngFor="let course of courses; even as isEven">
    {{ course.name }} <span *ngIf="isEven">(EVEN)</span>
  </li>
</ul>

<ul>
  <li *ngFor="let course of courses; odd as isOdd">
    {{ course.name }} <span *ngIf="isOdd">(ODD)</span>
  </li>
</ul>
```

<!--  ==========================================================================================  -->
<!--  ==========================================================================================  -->
<!--  ==========================================================================================  -->

# 2. ngFor and Change Detection
The code bellow allows modifing the array by adding item, removing item, or change item's value.

```
// File: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  courses = [
    { id: 1, name: 'course1'},
    { id: 2, name: 'course2'},
    { id: 3, name: 'course3'},
  ];

  onAdd() {
    this.courses.push({ id: 4, name: 'course4'});
  }

  onRemove(course: { id: number; name: string; }) {
    let index = this.courses.indexOf(course); <<<< Find index of object course in array courses
    this.courses.splice(index, 1); <<<<< Go to that index and remove 1 object
  }
  onChange(course: {id: number; name: string; }) {
    course.name = "UPDATED";
  }
}
```


```
<!-- File: app.component.html  -->
<button (click)="onAdd()">Add</button>

<ul>
  <li *ngFor="let course of courses; index as i">
    {{ i }} - {{ course.name }}
    <button (click)="onRemove(course)">Remove</button>
    <button (click)="onChange(course)">Change</button>
  </li>
</ul>
```
# 3. ngFor and TrackBy
## File: app.component.ts
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  courses: any ;

  loadCourses() {
    this.courses = [
      { id: 1, name: 'course1'},
      { id: 2, name: 'course2'},
      { id: 3, name: 'course3'},
    ];
  }
}
```
## File: app.component.
```
<button (click)="loadCourses()">Load Courses</button>

<ul>
  <li *ngFor="let course of courses">
    {{ course.name }}
  </li>
</ul>
```
Open browser inspect (F12), Every time button is clicked, the course list is loaded (reconstruction) to different memory location with the same value.<br>
TrackBy use to improve performance of the web page. If we load the same object to display on the page, TrackBy will skip loading it.<br>
Don’t need to use it for small object because we cannot see the different.<br>
Only use it for large object.<br>

## File: app.component.ts
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  courses: any ;

  loadCourses() {
    this.courses = [
      { id: 1, name: 'course1'},
      { id: 2, name: 'course2'},
      { id: 3, name: 'course3'},
    ];
  }

  trackCourse(course: any) {
    return course ? course.id : undefined;

  }
}
```
# File: app.component.html
```
<button (click)="loadCourses()">Load Courses</button>

<ul>
  <li *ngFor="let course of courses; TrackBy: trackCourse">
    {{ course.name }}
  </li>
</ul>
```
