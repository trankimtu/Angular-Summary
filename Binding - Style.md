
```
import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
    <button [style.backgroundColor]="isActive ? 'blue' : 'lightblue'">Save</button>
  `
})

export class CoursesComponent {
  isActive = true;
}
```
