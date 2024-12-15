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
