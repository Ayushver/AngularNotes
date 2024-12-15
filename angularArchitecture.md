# Core Angular Concepts

## 1. Angular Architecture
Angular follows a **component-based architecture**. Here are its core building blocks:

- **Components**: 
  - These are the basic building blocks of a UI in Angular. Each component has:
    - A **TypeScript file**: Contains logic and behavior (e.g., `app.component.ts`).
    - An **HTML template**: Defines the view (e.g., `app.component.html`).
    - A **CSS/SCSS file**: For styling (e.g., `app.component.css`).
  - Example:
    ```typescript
    import { Component } from '@angular/core';

    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })
    export class AppComponent {
      title = 'My Angular App';
    }
    ```

- **Modules**: 
  - A module is a container for components, directives, and services. The root module is called `AppModule` (`app.module.ts`).
  - Example:
    ```typescript
    import { NgModule } from '@angular/core';
    import { BrowserModule } from '@angular/platform-browser';
    import { AppComponent } from './app.component';

    @NgModule({
      declarations: [AppComponent],
      imports: [BrowserModule],
      providers: [],
      bootstrap: [AppComponent]
    })
    export class AppModule {}
    ```

- **Templates**: 
  - Define the structure and layout of a component using HTML. It can include Angular-specific syntax such as data binding and directives.

- **Directives**: 
  - **Structural Directives**: Modify the DOM structure (e.g., `*ngIf`, `*ngFor`).
  - **Attribute Directives**: Change the appearance or behavior of an element (e.g., `ngClass`, `ngStyle`).

- **Services**: 
  - These provide shared logic and data across components. Services use **Dependency Injection (DI)** to get instantiated.

- **Dependency Injection**: 
  - A design pattern used to inject dependencies (like services) into components, making them reusable and testable.

---

## 2. Component Lifecycle Hooks
Angular components have lifecycle hooks, which allow developers to add custom logic at different stages of a component's lifecycle:

- **`ngOnInit`**: Called once after the component is initialized.
- **`ngOnChanges`**: Invoked when the input properties of a component change.
- **`ngDoCheck`**: Runs during every change detection cycle.
- **`ngAfterContentInit`**: Triggered after content (e.g., `<ng-content>`) is projected into the view.
- **`ngAfterContentChecked`**: Runs after projected content has been checked.
- **`ngAfterViewInit`**: Called after the component's view (and child views) is initialized.
- **`ngAfterViewChecked`**: Invoked after the component's view (and child views) is checked.
- **`ngOnDestroy`**: Called before the component is destroyed (used for cleanup).

---

## 3. Data Binding
Angular provides four types of data binding to connect components to templates:

### a) Interpolation
- Syntax: `{{ expression }}`
- Used to display component data in the template.
- Example:
  ```html
  <h1>Welcome, {{ username }}!</h1>

  # Property Binding in Angular

# Property Binding in Angular

## What is Property Binding?
Property Binding in Angular is a way to bind data from a component to an element's property in the DOM. It is used to dynamically set values for properties of HTML elements or directives.

- **Syntax**: `[property]="expression"`
- The property in square brackets refers to the DOM property, not the HTML attribute.

---

## Why Use Property Binding?
- To dynamically control UI elements based on the component's data.
- It ensures the binding is reactive, so when the data changes, the view updates automatically.

---

## Example: Binding an Image Source
Here’s an example of using property binding to dynamically set the `src` attribute of an image:

### Component (TypeScript)
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-property-binding',
  templateUrl: './property-binding.component.html',
  styleUrls: ['./property-binding.component.css']
})
export class PropertyBindingComponent {
  imagePath: string = 'https://example.com/image.jpg';
  altText: string = 'Example Image';
}


<h2>Property Binding Example</h2>
<img [src]="imagePath" [alt]="altText" />

Here, [src] binds the imagePath property from the component to the src attribute of the <img> element.
Similarly, [alt] binds the altText property.


Example: Controlling Button Disabled State
You can use property binding to enable or disable a button dynamically.

Component (TypeScript)
typescript
Copy code
import { Component } from '@angular/core';

@Component({
  selector: 'app-property-binding',
  templateUrl: './property-binding.component.html',
  styleUrls: ['./property-binding.component.css']
})
export class PropertyBindingComponent {
  isDisabled: boolean = true;

  toggleButton() {
    this.isDisabled = !this.isDisabled;
  }
}
Template (HTML)
html
Copy code
<h2>Button Disabled State Example</h2>
<button [disabled]="isDisabled">Click Me</button>
<button (click)="toggleButton()">Toggle Disabled State</button>
[disabled] binds the isDisabled property to the button's disabled attribute.
Clicking the "Toggle Disabled State" button toggles the isDisabled value.
Key Points
Property Binding only works with DOM properties, not HTML attributes. For example:
[class] binds to the className property, not the class attribute.
The data flow is one-way, from the component to the DOM.



