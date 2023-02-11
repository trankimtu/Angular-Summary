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
  To get lorem paragraph, type “lorem” in html
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
  
