# Create dropdown
## File: app.component.html
```
<zippy title="Shipping Details">
  Shipping Details content
</zippy>

<zippy title="Billing Details">
  Billing Details content
</zippy>
```

## File: zippy.component.ts
```
import { Component, Input } from '@angular/core';

@Component({
  selector: 'zippy',
  templateUrl: './zippy.component.html',
  styleUrls: ['./zippy.component.css']
})
export class ZippyComponent {
  isExpanded: boolean | undefined;
  @Input('title') title: string | undefined;

  toggle() {
    this.isExpanded = !this.isExpanded; 
  }
}
```

## File: zippy.component.html
```
<div class="zippy">
    <div 
        class="zippy-heading"
        [class.expanded]="isExpanded"    
        (click) = "toggle()"
    >
        {{ title }}
    <i 
        class="bi"
        [ngClass]="{
            'bi-chevron-up': isExpanded,
            'bi-chevron-down': !isExpanded
        }"
    >
    </i>
    </div>
    <div *ngIf="isExpanded" class="zippy-body">
        <ng-content></ng-content>
    </div>
</div>
```

## File: zippy.component.css
```
.zippy {
    border: 1px solid #ccc;
    border-radius: 2px;
    width: 70%;
    margin: 20px;
}

.zippy-heading {
    font-weight: bold;
    padding: 20px;
    cursor: pointer;
}

.zippy-body {
    padding: 20px;
}

.expanded {
    background-color: #f0f0f0;
}

.bi {
    float: right;
}
```
