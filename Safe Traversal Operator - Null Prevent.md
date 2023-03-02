
```
// File: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  task = {
    title: 'Review application',
    assignee: {
      name: 'John Smith'
    }
  }
}

```


```
<!-- File: app.component.html -->
<span> {{ task.assignee.name }} </span>
```
Sometimes we’re dealing with complex object. It is possible that value of the property is NULL or Undefine.
```
// File: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  task = {
    title: 'Review application',
    assignee: {
      name: null  <<<<<<<<<<<<<<<<
    }
  }
}
```
To void this issue, we can use *ngIf to filter out the value.
```
<!-- File: app.component.html -->
<span *ngIf="task.assignee"> {{ task.assignee.name }} </span>
```
Or we can use other way by using safe traversal operator<br>
Because ```assignee``` can be null or undefine, we put “?” after it. (This gives error in my angular version)
In my version, doesn’t need the “?”
```
<!-- File: app.component.html -->
<span> {{ task.assignee?.name }} </span>
```

