# Built-in Pipes:
  1. Uppercase
  2. Lowercase
  3. Decimal: <number of integer digit> .<min number after dec> –<max number after dec point>
  4. Currency
  5. Percent
  For date, go to angular.io search for datepipe for more format 

  ```
  import { Component } from '@angular/core';

  @Component ({
    selector: 'courses',
    template: `
          {{ course.title | uppercase | lowercase}} <br>
          {{ course.rating | number:'1.1-1' }} <br>
          {{ course.students | number}} <br>
          {{ course.price | currency}} <br>
          {{ course.price | currency: 'AUD':true:'3.1-2'}} <br>
          {{ course.releaseDate | date:'shortDate'}}
    `
  })

  export class CoursesComponent {
    course = {
      title: "The Complete Angular Course",
      rating: 4.9745,
      students: 30123,
      price: 190.95,
      releaseDate: new Date(2016, 3, 1)
    }
  }

  ```
  
# Custom Pipe
  To get lorem paragraph, type “lorem” in html<br>
  
  ## Step 1: Declare pipe name
  In template interpolation {{ field | pipeName }}
  ```
  import { Component } from '@angular/core';

  @Component ({
    selector: 'courses',
    template: `
          {{ text | summary }}
    `
  })

  export class CoursesComponent {
    text = `
      Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
    `
  }

  ```
  ## Step 2: Code what the pipe does
  In summary.pipe.ts
  Get 1st 50 character then …
  ? after args means optional
  If value is empty, null, undefine will return null
  value.substr(0, 50) + ‘…’ : get 1st 50 characcter then add … after that
  ```
  import { Pipe, PipeTransform } from '@angular/core';

  @Pipe({
    name: 'summary'
  })
  export class SummaryPipe implements PipeTransform {
    transform(value: string, args?: any) {
        if (!value)
          return null;
        return value.substr(0, 50) + '...';
    }
  }
  ```
  ## Step3: Register SummaryPipe(class name) in app.module
  ```
  import { SummaryPipe } from './summary.pipe';
  @NgModule({
    declarations: [
      AppComponent,
      CoursesComponent,
      // CourseComponent
      SummaryPipe
    ],
  ```

  # Add more parameter to custom pipe
  If there’s limit, use limit else use 50<br>
  In this example we set limit = 10
  ```
  // course.component.ts
  import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
        {{ text | summary:10 }}
  `
})

export class CoursesComponent {
  text = `
    Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
  `
}
  ```

  summary.pipe.ts
  ```
  import { Pipe, PipeTransform } from '@angular/core';

  @Pipe({
    name: 'summary'
  })
  export class SummaryPipe implements PipeTransform {
    transform(value: string, limit?: number) {
        if (!value)
          return null;
    let actualLimit = (limit) ? limit : 50;
        return value.substr(0, actualLimit) + '...';
    }
  }

  ```
