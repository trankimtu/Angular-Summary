# A. File app.module.ts
Import app-routing.module
```
import { AppRoutingModule } from './app-routing.module';

```
File becomes:
```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';

import { PortfolioModule } from './portfolio/portfolio.module';
import { MusicModule } from './music/music.module';
import { UserLoginModule } from './user-login/user-login.module';



@NgModule({
  declarations: [
    AppComponent,
    CaptchaComponent,
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    UserLoginModule,
    MusicModule,
    PortfolioModule,
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```


# B. File app-routing.module.ts
```

```
