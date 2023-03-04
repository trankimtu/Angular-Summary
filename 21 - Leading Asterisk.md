Asterisk (*) is a shortcut way to write the code <br>
```
<div *ngIf="courses.length > 0; else noCourse">
  List of courses
</div>
```
Angular will rewrite the code as bellow:
```
<ng-template [ngIf]="courses.length > 0">
  <div>
    List of courses
  </div>
</ng-template>

<ng-template [ngIf]="!(courses.length > 0)">
  <div>
    No courses yet
  </div>
</ng-template>
```

Similar to *ngFor, *ng...
