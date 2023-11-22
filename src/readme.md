# Project: first Angular app

1. Ref: <https://angular.io/tutorial/first-app>

## First Angular app lesson 2 - Creating Components

1. Ref: <https://angular.io/tutorial/first-app/first-app-lesson-02>

### Step 1 - Create the HomeComponent

1. run "ng generate component home --inline-template --skip-tests"

### Step 2 - Add the new component to your app's layout

1 Import HomeComponent in src/app/app.component.ts
2 Add:

```typescript
import { Component } from '@angular/core';
import { HomeComponent } from './home/home.component';


@Component({
  selector: 'app-root',
  standalone: true,
  imports: [
    HomeComponent,
  ],
  template: `
  <main>
    <header class="brand-name">
      <img class="brand-logo" src="/assets/logo.svg" alt="logo" aria-hidden="true">
    </header>
    <section class="content">
      <app-home></app-home>
    </section>
  </main>
`,
  styleUrls: ['./app.component.css'],
})

export class AppComponent {
  title = 'homes';
}
```

### Step 3 - Add features to HomeComponent

## Lesson 3: Create the application’s HousingLocation component

1. Run `ng generate component housingLocation --inline-template --skip-tests`
2. Import HousingLocationComponent in src/app/home/home.component.ts

## First Angular app lesson 4 - Creating an interface

1. Run `ng generate interface housinglocation`

### Step 3 - Create a test house for your app

## Lesson 5: Add an input parameter to the component

### Step 1 - Import the Input decorator

## Lesson 8: Use *ngFor to list objects in component

## Lesson 09: Angular services

1. Run: `ng generate service housing --skip-tests`

### Step 2 - Add static data to the new service

## Lesson 10: Add routes to the application

1. Step 1 - Create a default details component
2. Run: `ng generate component details --inline-template --skip-tests`
3. Step 2 - Add routing to the application
4. Step 3 - Add route to new component

## Lesson 11 - Integrate details page into application

1. Step 1 - Create a new service for your app
2. Step 2 <https://angular.io/tutorial/first-app/first-app-lesson-11#lesson-11---integrate-details-page-into-application>

## Lesson 12: Adding a form to your Angular app

1. Add to service

```Typescript
submitApplication(firstName: string, lastName: string, email: string) {
  console.log(`Homes application received: firstName: ${firstName}, lastName: ${lastName}, email: ${email}.`);
}
```

1. Link <https://angular.io/tutorial/first-app/first-app-lesson-12#lesson-12-adding-a-form-to-your-angular-app>

## TODO

## Lesson 13: Add the search feature to your app

## Lesson 14: Add HTTP communication to your app

## ALL DONE
