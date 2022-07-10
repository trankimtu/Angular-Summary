# app.component.html
```
<like 
  [is-like] = "post.isLike" 
  [like-count] = "post.likeCount"
  (like-change) = "onLikeChanged()" 
></like>
```
# app.component.ts
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = '05_BuildingReusableComponent';

  post = {
    isLike : false,
    likeCount: 100
  }

  onLikeChanged() {
    console.log("Event is raised!");
  }
}









```
# like.component.html
```
<i 
    class="bi m-5"
    [class.bi-heart] = "!isLike"
    [class.bi-heart-fill] = "isLike"
    (click) = onClick();
></i>
{{ likeCount }}

```






# like.component.ts
```
import { Component, EventEmitter, Input, OnInit, Output } from '@angular/core';

@Component({
  selector: 'like',
  templateUrl: './like.component.html',
  styleUrls: ['./like.component.css']
})
export class LikeComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }


  @Input('is-like') isLike : boolean | undefined;
  @Input('like-count') likeCount : number | undefined;

  @Output('like-change') likeChange = new EventEmitter(); 
  
  onClick() {
    this.isLike = !this.isLike;
    this.likeChange.emit();
  }
}
```
