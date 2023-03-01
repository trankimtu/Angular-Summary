# Class Binding
```
// File: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  isSelected = false;
  
  onClick() {
    this.isSelected = !this.isSelected;

  }
}
```


```
<!-- File: app.component.html -->
<i
  class="bi"
  [class.bi-star-fill] = "isSelected" 
  [class.bi-star] = "!isSelected"
  (click)="onClick()"
>
</i>
```

# Instead use class binding twice, we can use ngClass directive
Using ```key``` represent class and ```value``` as value<br>
This is an example of attribute directive which uses to modify attribute of an existing DOM element
```
<!-- File: app.component.html -->
<i
  class="bi"
  [ngClass]="{
    'bi-star-fill': isSelected,
    'bi-star': !isSelected
  }"
  (click)="onClick()"
>
</i>
```
