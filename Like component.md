# like.component.css
```
.bi {
    color: #ccc;
    cursor: pointer;
}
.highlighted {
    color: deeppink;
}
```
<!-- ====================================================== -->

# like.component.html
```
<i 
    class="bi bi-heart-fill"
    [class.highlighted]="isActive"    
    (click) = "onClick()"
></i>

<span> {{ likesCount }} </span>
```
<!-- ====================================================== -->

# like.component.ts
```
import { Component, Input } from '@angular/core';

@Component({
  selector: 'like',
  templateUrl: './like.component.html',
  styleUrls: ['./like.component.css']
})
export class LikeComponent {

  @Input('likesCount') likesCount = 0;
  @Input('isActive') isActive : boolean | undefined;

  onClick() {
    this.likesCount += (this.isActive) ? -1 : 1;
    this.isActive = !this.isActive;
  }
}
```
<!-- ====================================================== -->

# app.component.html
```
<like
    [likesCount]="tweet.likesCount"
    [isActive]="tweet.isLiked"
></like>
```
<!-- ====================================================== -->

# app.component.ts
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = '05_soultion';
  tweet = {
    body:'...',
    likesCount: 10,
    isLiked: true
  }
}
```



