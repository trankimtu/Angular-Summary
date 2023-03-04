

```
// file: courses.service.ts

export class CoursesService {
    getCourses() {
        return ["course1", "course2", "course3"];
    }
}

```

## Constructor set courses by call CoursesService method
```
// file: courses.component.ts

import { Component } from '@angular/core';
import { CoursesService } from './courses.service';

// Decorator Function
@Component({
    selector: 'courses',
    template: `
        <h2> {{ title }}</h2>
        <ul>
        <li *ngFor="let course of courses">
            {{ course }}
        </li>
        </ul>
    `
})            

export class CoursesComponent {
    title = "List of courses";
    courses; // Need Dependency Injection 

    constructor() {
        let service = new CoursesService();
        this.courses = service.getCourses;
    }
}

```

