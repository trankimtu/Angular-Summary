
Use class binding for "active" <br>
Click method call function and define viewMode in that function. However, the function has only one line so we in line it here. Do not need to create a method for this. <br>
In the tag ```<div *ngSwitchCase="'map'">``` : “  ” for directive,  ‘   ’ for value map as a string <br>

# File: app.component.ts
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
   viewMode ='map';
}
```

# File: app.component.html
```
<ul class="nav nav-pills">
  <li class="nav-item">
    <a 
      class="nav-link"
      [class.active] ="viewMode == 'map'" 
      (click)="viewMode='map'"
    >
      Map View
    </a>
  </li>

  <li 
    class="nav-item">
    <a 
      class="nav-link"
      [class.active] ="viewMode == 'list'" 
      (click)="viewMode='list'"
    >
      List View
    </a>
  </li>
</ul>

<div [ngSwitch]="viewMode">
  <div *ngSwitchCase="'map'">Map View Content</div>
  <div *ngSwitchCase="'list'">List View Content</div>
  <div *ngSwitchDefault>Otherwise</div>
</div>
```
