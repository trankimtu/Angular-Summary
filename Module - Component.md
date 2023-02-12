# Module
<ul>
  <li>A container that groups related components. </li>
  <li>All Angular app has App module</li>
  <li>Inside App module there can be many modules, each of them responds to each area of the application such as Courses module, Messaging module, Instructor module, and Admin module</li>
</ul>

# Component
Every Angular has a tree component start with Root component (App component)<br>
## 3 steps create component:

### Step 1: Create a component
In src/app<br>
Create courses. component.ts<br>
```
// file: courses.component.ts

import { Component } from '@angular/core';

// Decorator Function
@Component ({
  // Base on CSS
  // "courses"  for <courses>                  
  // ".courses" for <div class="courses"       
  // "#courses" for <div id="courses"          

  selector: 'courses',
  template: '<h2>Courses</h2>' 
})
export class CoursesComponent {

}
```

