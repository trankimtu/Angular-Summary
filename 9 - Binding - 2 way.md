# File app.module.ts
```
import { FormsModule } from '@angular/forms';

imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule,
    NgModule
  ],

```
# File course.component.ts
```
import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
    <input [(ngModel)]="email" (keyup.enter)="onKeyUp()" />
  `
})

export class CoursesComponent {
  email = "me@ex.com";
  onKeyUp() {
    console.log(this.email);
  }
}
```
