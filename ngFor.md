1. Export value index of the array to alias local valuable i 
# File: app.component.ts
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
# File: app.component.html 
```
<ul>
  <li *ngFor="let course of courses; index as i">
    {{ i }} - {{ course.name }}
  </li>
</ul>
```
2. Beside index, there are many other value we can export
Visit angular.io, search for “ngForOf”. Select “D(Directive) NgForOf”
[https://angular.io/api/common/NgForOf](https://angular.io/api/common/NgForOf)
•	index: number: The index of the current item in the iterable.
•	count: number: The length of the iterable.
•	first: boolean: True when the item is the first item in the iterable.
•	last: boolean: True when the item is the last item in the iterable.
•	even: boolean: True when the item has an even index in the iterable.
•	odd: boolean: True when the item has an odd index in the iterable.
# File: app.component.ts
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
# File: app.component.html 
```
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
