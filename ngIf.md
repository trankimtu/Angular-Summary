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
