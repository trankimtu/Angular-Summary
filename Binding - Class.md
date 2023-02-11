# Class Binding
## like.component.ts
```
import { Component, OnInit} from '@angular/core';

@Component({
  selector: 'like',
  templateUrl: './like.component.html',
  styleUrls: ['./like.component.css']
})
export class LikeComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

  isLike = false;
  
  onClick() {
    this.isLike = !this.isLike;
  }
}
```

## like.component.html
```
<i 
    class="bi"
    [class.bi-heart]="!isLike"
    [class.bi-heart-fill]="isLike"
    (click)="onClick()"
></i>
```
