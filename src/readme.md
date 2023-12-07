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

### Step 1 - Update the home component properties

1. Ref: <https://angular.io/tutorial/first-app/first-app-lesson-13#step-1---update-the-home-component-properties>
2. File `home.component.ts`
3. Add: New property: `filteredLocationList: HousingLocation[] = [];`
4. Set values:

```TypeScript
  constructor() {
    this.housingLocationList = this.housingService.getAllHousingLocations();
    this.filteredLocationList = this.housingLocationList;   // <==
  }
```

### Step 2 - Update the home component template

1. home.component.ts
2. Add a template variable to HomeComponent's template
3. Add: `<input type="text" placeholder="Filter by city" #filter>`
4. Bind the click event
5. Add: `<button class="primary" type="button" (click)="filterResults(filter.value)">Search</button>`
6. Update the ngFor directive value
7. Add: <app-housing-location *ngFor="let housingLocation of filteredLocationList" [housingLocation]="housingLocation"></app-housing-location>`

### Step 3 - Implement the event handler function

1. Add the filterResults function implementation
2. Add

```typescript
filterResults(text: string) {
  if (!text) {
    this.filteredLocationList = this.housingLocationList;
    return;
  }

  this.filteredLocationList = this.housingLocationList.filter(
    housingLocation => housingLocation?.city.toLowerCase().includes(text.toLowerCase())
  );
}
```

## Lesson 14: Add HTTP communication to your app

### Step 1 - Configure the JSON server

1. run `npm install -g json-server`
2. run `json-server --watch db.json`
3. ref <https://www.npmjs.com/package/json-server>
4. In root add db.json

### Step 2 - Update service to use web server instead of local array

1. `url = 'http://localhost:3000/locations'; //home.servce.ts`
2. file getAllHousingLocations update getAllHousingLocations
3. update `async getHousingLocationById(id: number): Promise<HousingLocation`
4. Final version of housing.service.ts

```typescript
import { Injectable } from '@angular/core';
import { HousingLocation } from './housinglocation';

@Injectable({
  providedIn: 'root'
})
export class HousingService {

  url = 'http://localhost:3000/locations';

  async getAllHousingLocations(): Promise<HousingLocation[]> {
    const data = await fetch(this.url);
    return await data.json() ?? [];
  }

  async getHousingLocationById(id: number): Promise<HousingLocation | undefined> {
    const data = await fetch(`${this.url}/${id}`);
    return await data.json() ?? {};
  }

  submitApplication(firstName: string, lastName: string, email: string) {
    console.log(firstName, lastName, email);
  }
}
```

### Step 3 - Update the components to use asynchronous calls to the housing service

```Typescript
//home.component.ts
constructor() {
  this.housingService.getAllHousingLocations().then((housingLocationList: HousingLocation[]) => {
    this.housingLocationList = housingLocationList;
    this.filteredLocationList = housingLocationList;
  });
}

//details.component.ts
constructor() {
  const housingLocationId = parseInt(this.route.snapshot.params['id'], 10);
  this.housingService.getHousingLocationById(housingLocationId).then(housingLocation => {
    this.housingLocation = housingLocation;
  });
}

## ALL DONE
