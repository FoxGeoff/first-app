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