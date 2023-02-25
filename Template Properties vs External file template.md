# Template Properties vs External File template
If the component template's code has 5 lines or less, use template properties<br>
Else, use external file template<br>
All the external template is compiled and translate to js. No separate request to download the template

```
// file: Favorite.component.ts
import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'favorite',
  // templateUrl: './favorite.component.html',
  template: `
    <i
      class="bi"
      [class.bi-star-fill] = "isSelected" 
      [class.bi-star] = "!isSelected"
      (click)="onClick()"
    >
    </i>`,

  styleUrls: ['./favorite.component.css']
})
export class FavoriteComponent implements OnInit {

  @Input('is-favorite') isSelected = false;
  @Output('change') click = new EventEmitter();
  constructor() { }
  ngOnInit(): void {
  }
  
  onClick() {
    this.isSelected = !this.isSelected;

    // Pass an object
    this.click.emit({ newValue: this.isSelected });
  }
}

export interface FavoriteChangedEventArgs {
  newValue: boolean
}
```
