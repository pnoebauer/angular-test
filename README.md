# Angular vs React Component Comparison

## React

### React Parent Component

```jsx
import React from 'react';
import ChildComponent from './ChildComponent';

export default ParentComponent extends React.Component {
  render() {
    return (
      <div>
        <ChildComponent someprop={123} />
      </div>
    );
  }
}
```

### React Child Component

```jsx
import React from "react";

export default class ChildComponent extends React.Component {
  render() {
    return <div>This inserts the parent prop: {this.props.someprop}!</div>;
  }
}
```

## Angular

### Angular Parent Component

```ts
import { Component } from "@angular/core";

@Component({
  selector: "app-parent",
  template: ` <app-child [someprop]="currentItem"></app-child> `,
})
export class ParentComponent {
  currentItem = 123;
}
```

### Angular Child Component

```ts
import { Component, Input } from "@angular/core";

@Component({
  selector: "app-child",
  template: ` <div>This inserts the parent prop: {{ someprop }}!</div> `,
})
export class ChildComponent {
  @Input() someprop!: number;
}
```

# Angular vs React Looping

## React JSX Syntax for Looping

```jsx
{
  housingLocationList.map((housingLocation) => <HousingLocation housingLocation={housingLocation} />);
}
```

## Angular \*ngFor Directive

```html
<app-housing-location *ngFor="let housingLocation of housingLocationList" [housingLocation]="housingLocation"> </app-housing-location>
```

# Angular Injection vs React

## React JSX Syntax for Looping

```jsx
{
  housingLocationList.map((housingLocation) => <HousingLocation housingLocation={housingLocation} />);
}
```

## Angular \*ngFor Directive

```html
<app-housing-location *ngFor="let housingLocation of housingLocationList" [housingLocation]="housingLocation"> </app-housing-location>
```

# Angular vs React Logging Higher-Order Component (HOC) and Injectable Service

## React withLogger Higher-Order Component (HOC)

```jsx
function withLoggerService(WrappedComponent) {
  return function WithLogger(props) {
    console.log("Component rendered:", WrappedComponent.name);
    return <WrappedComponent {...props} />;
  };
}

// Usage
const EnhancedComponent = withLogger(MyComponent);

// Wrapped Component
class MyComponent extends React.Component {
  render() {
    return <div>This is my component</div>;
  }
}
```

## Angular Injectable Service

```ts
// Service Definition
import { Injectable } from "@angular/core";

@Injectable({
  providedIn: "root",
})
export class LoggerService {
  logComponentRender(componentName: string) {
    console.log(`Component rendered: ${componentName}`);
  }
}

// Component Usage
import { Component } from "@angular/core";
import { LoggerService } from "./logger.service";

@Component({
  selector: "app-my-component",
  template: "<p>This is my component</p>",
})
export class MyComponent {
  loggerService: LoggerService = inject(LoggerService);
   constructor() {
    this.loggerService.logComponentRender("MyComponent");
  }
}
```
