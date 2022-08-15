## How to respond to input changes reactively in the child component

Component interaction can work in one of the following three ways:
 - `ngOnChanges()` lifecycle hooks
 - Setters on the `@Input()` property
 - Services

If your component is a presentational component and interacts only with the `@Input()` and `@Output()` properties, then using ***setters is the most reactive way* **of interacting with the child component

Let's understand how!

## Parent Child Component Interaction

Parent component passes value to the child component with the following syntax where userValue is an [@Input()](https://angular.io/api/core/Input) property in the child component
```
<child-component [userValue]="userValue"></child-component>
```
```
export class ChildComponent {
  @Input() userValue;
}
```

## Setters on the `@Input()` property

Setters on the [@Input()](https://angular.io/api/core/Input) property runs some additional logic whenever the input changes.
So, instead of defining userValue, we define a function on the userValue property which executes whenever input changes.
```
export class ChildComponent {
  status = false;
  @Input() set userValue(value: string) {
      this.status = true;
  }
}
```
These are called property accessor methods which executes on setting/getting values. Add a `set` keyword before a property to make a setter.

----

## Thanks for reading!

Please feel free to reach out on [Twitter](https://twitter.com/devminibhati) or [LinkedIn](https://www.linkedin.com/in/minibhati93/)