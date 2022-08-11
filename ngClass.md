# File: app.component.ts
```
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
# File: app.component.html
```
<i
  class="bi"
  [class.bi-star-fill] = "isSelected" 
  [class.bi-star] = "!isSelected"
  (click)="onClick()"
>
</i>
```

# Instead use class binding twice, we can use ngClass directive
# File: app.component.html
```
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
