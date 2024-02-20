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
import React from 'react';

export default class ChildComponent extends React.Component {
  render() {
    return (
      <div>
        This inserts the parent prop: {this.props.someprop}!
      </div>
    );
  }
}
```

## Angular

### Angular Parent Component
```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-parent',
  template: `
    <app-child [someprop]="currentItem"></app-child>
  `
})
export class ParentComponent {
  currentItem = 123;
}
```

### Angular Child Component
```ts
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `
    <div>
      This inserts the parent prop: {{ someprop }}!
    </div>
  `
})
export class ChildComponent {
  @Input() someprop!: number;
}

```