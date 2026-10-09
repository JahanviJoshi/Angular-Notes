# Angular-Notes

# Angular Fundamentals — 4 Years Experience

> **Target:** 4 Years Experience  
> **Focus:** Interview + Real Project Understanding  
> **Stack:** Angular + .NET API

---

# 1. What is Angular?

### What is it?

Angular is a **TypeScript-based frontend framework** developed by Google for building **single-page applications (SPAs)**.

Angular provides a complete structure for building applications using concepts such as:

- Components
- Templates
- Data binding
- Dependency Injection
- Services
- Routing
- Forms
- HTTP communication
- Directives
- Pipes
- Modules

Unlike using plain JavaScript or a lightweight library, Angular provides an **opinionated application structure**, which makes it suitable for large and enterprise applications.

### Why do we use it?

We use Angular to:

- Build dynamic web applications.
- Create reusable UI components.
- Communicate with backend APIs.
- Manage application state and data.
- Implement routing/navigation.
- Perform form validation.
- Maintain large applications with a structured architecture.
- Improve code reusability and maintainability.

### Real project example

Suppose we have a **Membership Management System**.

The Angular application may contain:

```text
Login
   ↓
Dashboard
   ↓
Member Management
   ├── Member List
   ├── Add Member
   ├── Edit Member
   └── Member Details
```

Angular components handle the UI, services communicate with the .NET APIs, and routing handles navigation.

For example:

```text
Angular
   ↓
MemberComponent
   ↓
MemberService
   ↓
.NET Web API
   ↓
MySQL
```

### Code example

A simple Angular component:

```typescript
@Component({
  selector: 'app-member',
  template: `
    <h2>Member Management</h2>
  `
})
export class MemberComponent {

}
```

### Interview answer

> **Angular is a TypeScript-based frontend framework developed by Google for building scalable single-page applications. It provides features like component-based architecture, data binding, dependency injection, routing, forms, directives, and HTTP communication, which makes it suitable for developing large enterprise applications.**

### Common mistake

❌ Saying:

> Angular is a JavaScript library.

Angular is a **framework**, not just a library.

❌ Saying Angular is only used for UI.

Angular also provides application-level features such as routing, dependency injection, forms, HTTP communication, and application architecture.

---

# 2. Difference Between Angular and AngularJS

### What is it?

**AngularJS** refers to the older Angular framework, mainly based on JavaScript.

**Angular** refers to the modern framework that was completely redesigned and is primarily based on TypeScript.

AngularJS and Angular are **not simply different versions of the same architecture**. Angular was a major rewrite.

### Why do we use it?

Understanding the difference is important because interviewers often ask this when they see Angular experience on a resume.

### Real project example

An older application might use:

```text
AngularJS
Controllers
$scope
Two-way binding
```

A modern Angular application typically uses:

```text
Angular
Components
Services
Dependency Injection
TypeScript
RxJS
Routing
```

### Code example

#### AngularJS

```javascript
app.controller('MemberController', function($scope) {

    $scope.memberName = "John";

});
```

#### Angular

```typescript
export class MemberComponent {

  memberName = "John";

}
```

Template:

```html
<h2>{{ memberName }}</h2>
```

### Interview answer

> **AngularJS is the older JavaScript-based framework, whereas Angular is the modern TypeScript-based framework that was redesigned from the ground up. Angular uses component-based architecture, improved dependency injection, TypeScript, better tooling, and improved support for large-scale applications.**

### Common mistake

❌ Saying:

> Angular is just AngularJS with a newer version.

Angular is a major architectural rewrite.

---

# 3. What is a Component in Angular?

### What is it?

A **Component** is one of the fundamental building blocks of an Angular application.

A component controls a specific part of the UI.

A component generally contains:

```text
Component
├── TypeScript class
├── HTML template
└── CSS/SCSS styles
```

The TypeScript class contains the component's logic and data, while the template defines what is displayed on the screen.

### Why do we use it?

Components help us:

- Break a large UI into smaller pieces.
- Reuse UI functionality.
- Separate business/UI responsibilities.
- Make applications easier to maintain and test.

### Real project example

In a Membership Management application:

```text
MemberListComponent
MemberAddComponent
MemberEditComponent
MemberDetailsComponent
LoginComponent
DashboardComponent
```

Each component has a specific responsibility.

For example:

```text
MemberListComponent
        ↓
Displays members
        ↓
Calls MemberService
        ↓
Gets data from .NET API
```

### Code example

```typescript
@Component({
  selector: 'app-member',
  templateUrl: './member.component.html',
  styleUrls: ['./member.component.css']
})
export class MemberComponent {

  memberName = 'John';

}
```

HTML:

```html
<h2>Member Name: {{ memberName }}</h2>
```

### Interview answer

> **A component is a fundamental building block of Angular applications. It controls a specific part of the UI and consists of a TypeScript class, template, and styles. Components help us divide the application into reusable and maintainable UI sections.**

### Common mistake

❌ Thinking that a component contains only HTML.

A component combines:

- UI template
- Component logic
- Styling
- Metadata/configuration

---

# 4. What is a Module (NgModule)?

### What is it?

An **NgModule** is a mechanism used to organize Angular applications by grouping related Angular components, directives, pipes, and services.

It is defined using the `@NgModule` decorator.

> **Important for modern Angular:** Standalone components are now also supported and are increasingly common. Therefore, don't assume every modern Angular application must use `NgModule`. However, many enterprise/legacy Angular applications still use modules.

### Why do we use it?

NgModules help organize large applications into logical sections.

For example:

```text
Application
│
├── CoreModule
├── SharedModule
├── MemberModule
└── AdminModule
```

This makes large applications easier to maintain.

### Real project example

A membership application might have:

```text
MemberModule
│
├── MemberListComponent
├── MemberAddComponent
├── MemberEditComponent
└── MemberDetailsComponent
```

All member-related functionality can be grouped together.

### Code example

```typescript
@NgModule({
  declarations: [
    MemberComponent
  ],
  imports: [
    CommonModule
  ]
})
export class MemberModule {

}
```

### Interview answer

> **NgModule is an Angular mechanism used to organize related components, directives, pipes, and services into cohesive functional areas. It helps structure larger applications. However, modern Angular also supports standalone components, so NgModules are no longer mandatory for every application.**

### Common mistake

❌ Saying:

> Every Angular application must use NgModules.

Modern Angular supports **standalone components**, so this statement is outdated.

---

# 5. What is a Root Module (AppModule)?

### What is it?

`AppModule` traditionally acts as the **root NgModule** of an Angular application.

It is the starting point from which Angular bootstraps the application.

In older/module-based Angular applications, `AppModule` commonly contains:

- Root component
- Required imports
- Application-level providers
- Bootstrap configuration

### Why do we use it?

It provides the starting structure for a module-based Angular application.

### Real project example

A traditional Angular application might look like:

```text
AppModule
   ↓
AppComponent
   ↓
Router
   ↓
Feature Components
```

For example:

```text
AppModule
 ├── AppComponent
 ├── MemberModule
 ├── AdminModule
 └── SharedModule
```

### Code example

Traditional Angular application:

```typescript
@NgModule({
  declarations: [
    AppComponent
  ],

  imports: [
    BrowserModule,
    AppRoutingModule
  ],

  providers: [],

  bootstrap: [
    AppComponent
  ]
})
export class AppModule {

}
```

### Interview answer

> **AppModule is traditionally the root NgModule of a module-based Angular application. It acts as the entry point for bootstrapping the root component and configuring application-level dependencies. In modern Angular, standalone bootstrapping can be used instead, so AppModule is not mandatory.**

### Common mistake

❌ Saying:

> AppModule is mandatory in every Angular application.

Modern Angular applications can use standalone bootstrapping.

---

# 6. What is a Feature Module?

### What is it?

A **Feature Module** is an NgModule created to group functionality related to a specific business feature.

For example:

```text
MemberModule
OrderModule
PaymentModule
AdminModule
```

Each module contains functionality related to that feature.

### Why do we use it?

Feature modules help:

- Organize large applications.
- Separate business functionality.
- Improve maintainability.
- Support lazy loading.
- Reduce complexity in the root application structure.

### Real project example

In a Membership Management application:

```text
MemberModule
│
├── MemberListComponent
├── MemberDetailsComponent
├── MemberAddComponent
├── MemberEditComponent
├── MemberService
└── MemberRoutingModule
```

The member-related functionality stays together.

If the Member feature is lazy-loaded, Angular can load it only when the user navigates to the member section.

### Code example

```typescript
@NgModule({
  declarations: [
    MemberListComponent,
    MemberDetailsComponent
  ],

  imports: [
    CommonModule,
    MemberRoutingModule
  ]
})
export class MemberModule {

}
```

### Interview answer

> **A feature module groups components, directives, pipes, and related functionality belonging to a specific business feature. For example, in a membership application, MemberModule can contain member-related components and routing. Feature modules improve organization and can also support lazy loading.**

### Common mistake

❌ Creating one huge module containing every component in the application.

Large applications should be organized around meaningful features.

---

# 7. What is a Component Decorator?

### What is it?

The `@Component` decorator provides metadata that tells Angular that a TypeScript class should be treated as a component.

It defines information such as:

- Component selector
- Template
- Styles
- Other component metadata

### Why do we use it?

Without the appropriate component metadata, Angular would not know:

- Which class represents the component.
- Which HTML template belongs to it.
- Which selector should be used.
- Which styles belong to the component.

### Real project example

For a member component:

```typescript
@Component({
  selector: 'app-member',
  templateUrl: './member.component.html',
  styleUrls: ['./member.component.css']
})
export class MemberComponent {

}
```

The selector:

```html
<app-member></app-member>
```

can then be used to render the component.

### Code example

```typescript
@Component({
  selector: 'app-dashboard',
  template: `
    <h1>Dashboard</h1>
  `
})
export class DashboardComponent {

}
```

### Interview answer

> **The @Component decorator provides metadata that tells Angular how to create and render a component. It defines information such as the selector, template, and styles associated with the component class.**

### Common mistake

❌ Saying:

> `@Component` is the component itself.

The TypeScript class represents the component logic, while `@Component` provides Angular metadata describing how that class should be treated as a component.

---

# 8. What is a Template in Angular?

### What is it?

A **template** is the HTML structure that defines the UI of an Angular component.

Angular templates are more powerful than normal HTML because they support Angular features such as:

- Interpolation
- Property binding
- Event binding
- Structural/control flow
- Directives
- Pipes
- Template expressions

### Why do we use it?

Templates allow us to connect the component's data and logic with the UI.

### Real project example

Suppose the component contains:

```typescript
memberName = 'John';
```

The template can display it:

```html
<h2>{{ memberName }}</h2>
```

If the value changes, Angular updates the UI accordingly.

### Code example

```typescript
export class MemberComponent {

  memberName = 'John';

  isActive = true;

}
```

Template:

```html
<h2>{{ memberName }}</h2>

<button [disabled]="!isActive">
  Edit Member
</button>
```

### Interview answer

> **An Angular template defines the UI of a component using HTML enhanced with Angular template syntax. It allows us to display component data and interact with the component through binding, events, directives, control flow, and pipes.**

### Common mistake

❌ Thinking templates are only static HTML.

Angular templates can dynamically interact with component data and user events.

---

# 9. What is Data Binding?

### What is it?

**Data binding** is the mechanism that connects the component's data/logic with the template/UI.

It allows information to move between:

```text
Component Class
       ↕
    Template
```

For example:

```typescript
memberName = "John";
```

can be displayed in HTML using:

```html
{{ memberName }}
```

### Why do we use it?

Data binding helps us:

- Display dynamic data.
- Pass data to UI elements.
- Respond to user events.
- Synchronize form values with component data.

Without data binding, we would need to manually manipulate the DOM for many UI updates.

### Real project example

Suppose the API returns:

```json
{
  "id": 101,
  "name": "John",
  "isActive": true
}
```

The Angular component stores this data:

```typescript
member = {
  id: 101,
  name: 'John',
  isActive: true
};
```

The template can display:

```html
<h2>{{ member.name }}</h2>
```

And bind the active status:

```html
<input type="checkbox" [checked]="member.isActive">
```

### Code example

```html
<!-- Component → Template -->
<h2>{{ member.name }}</h2>

<!-- Template → Component -->
<button (click)="deleteMember()">
  Delete
</button>

<!-- Two-way -->
<input [(ngModel)]="member.name">
```

### Interview answer

> **Data binding is the mechanism Angular provides to establish communication between a component class and its template. It allows us to display component data, bind properties, handle user events, and synchronize UI values with component state.**

### Common mistake

❌ Saying data binding means only interpolation.

Interpolation is only **one type** of Angular data binding.

---

# 10. Types of Data Binding

### What is it?

Angular primarily provides four commonly discussed types of data binding:

```text
1. Interpolation
2. Property Binding
3. Event Binding
4. Two-Way Binding
```

---

## 10.1 Interpolation

### What is it?

Interpolation displays component data in the HTML using:

```html
{{ expression }}
```

### Code example

```typescript
memberName = 'John';
```

```html
<h2>{{ memberName }}</h2>
```

### Real project example

Displaying a logged-in user's name:

```html
Welcome, {{ userName }}
```

### Interview answer

> **Interpolation is used to display component data in the template using double curly braces.**

---

## 10.2 Property Binding

### What is it?

Property binding binds a component value to a DOM element or Angular component property.

Syntax:

```html
[property]="expression"
```

### Code example

```typescript
isDisabled = true;
```

```html
<button [disabled]="isDisabled">
  Save
</button>
```

### Real project example

Disable the Save button while an API request is running:

```typescript
isSaving = true;
```

```html
<button [disabled]="isSaving">
  Save Member
</button>
```

### Interview answer

> **Property binding allows us to dynamically set a DOM or component property using a value from the component.**

---

## 10.3 Event Binding

### What is it?

Event binding allows the template to send user actions/events to the component.

Syntax:

```html
(event)="method()"
```

### Code example

```html
<button (click)="deleteMember()">
  Delete
</button>
```

Component:

```typescript
deleteMember() {
  console.log('Member deleted');
}
```

### Real project example

When the user clicks Delete:

```text
User clicks Delete
       ↓
(click)
       ↓
deleteMember()
       ↓
API call
       ↓
Delete member
```

### Interview answer

> **Event binding allows Angular to respond to events generated by the user or DOM, such as click, input, change, and submit events.**

---

# 10.4 Two-Way Data Binding

### What is it?

Two-way binding allows data to flow in **both directions**:

```text
Component
   ↕
Template
```

Angular commonly uses:

```html
[(ngModel)]
```

This syntax is called **banana-in-a-box syntax**.

### Code example

```typescript
memberName = 'John';
```

```html
<input [(ngModel)]="memberName">

<p>{{ memberName }}</p>
```

If the user changes the input:

```text
Input
  ↓
memberName updated
  ↓
UI updated
```

### Real project example

For editing a member:

```html
<input [(ngModel)]="member.name">
```

When the user changes the name, the component's `member.name` is updated.

### Interview answer

> **Two-way data binding keeps the component value and UI value synchronized. In template-driven forms, Angular commonly provides this through [(ngModel)].**

### Common mistake

❌ Saying:

> Two-way binding is always the best approach.

For large enterprise applications, especially complex forms, **Reactive Forms** are often preferred because they provide stronger programmatic control, validation, and testability.

---

# Data Binding — Quick Interview Table

| Binding Type | Direction | Syntax | Example |
|---|---|---|---|
| Interpolation | Component → Template | `{{ }}` | `{{member.name}}` |
| Property Binding | Component → Template | `[ ]` | `[disabled]="isDisabled"` |
| Event Binding | Template → Component | `( )` | `(click)="save()"` |
| Two-Way Binding | Component ↔ Template | `[( )]` | `[(ngModel)]="name"` |

---

# ⭐ 4-Year Experience Interview Scenario

### Scenario

**Interviewer:**  
You have a Save button in your Angular application. While the API request is running, the button should be disabled. How would you implement it?

### Answer

I would maintain a loading state in the component:

```typescript
isSaving = false;

saveMember() {

  this.isSaving = true;

  this.memberService.saveMember(this.member)
    .subscribe({
      next: () => {
        this.isSaving = false;
      },
      error: () => {
        this.isSaving = false;
      }
    });
}
```

Template:

```html
<button
  [disabled]="isSaving"
  (click)="saveMember()">
  Save
</button>
```

Here:

- `[disabled]` → **Property Binding**
- `(click)` → **Event Binding**
- `isSaving` → Component state

### Why is this a good 4-year answer?

Because instead of only defining property binding, you're showing how Angular binding is used in a **real application scenario**.

---

# ⭐ Important 4-Year Experience Points

Remember these connections:

```text
Angular
   ↓
Component
   ↓
Template
   ↓
Data Binding
   ├── Interpolation
   ├── Property Binding
   ├── Event Binding
   └── Two-Way Binding
```

And for application architecture:

```text
Angular Application
        ↓
Root / Bootstrap
        ↓
Features
        ↓
Components
        ↓
Services
        ↓
.NET Web API
```

### Modern Angular point

For interviews, be aware that Angular has evolved beyond the traditional `AppModule`/`NgModule` architecture.

Modern Angular supports:

- Standalone components
- Standalone bootstrapping
- Modern control-flow syntax
- Signals
- Functional APIs

# Angular Data Binding, Directives, Pipes & Dependency Injection

> **Target:** 4 Years Experience
> **Focus:** Interview + Real Project Understanding
> **Stack:** Angular + .NET Web API

---

# 1. What is Interpolation?

### What is it?

**Interpolation** is used to display component data inside an Angular template.

It uses double curly braces:

```html
{{ expression }}
```

The data flows from:

```text
Component
    ↓
Template
```

### Why do we use it?

We use interpolation when we want to display dynamic values in the UI.

Common examples:

- Display username
- Display member name
- Display API response
- Display calculated values
- Display status messages

### Real project example

Suppose our component receives member information from an API:

```typescript
memberName = 'John';
membershipType = 'Premium';
```

Template:

```html
<h2>{{ memberName }}</h2>
<p>Membership: {{ membershipType }}</p>
```

The UI displays:

```text
John
Membership: Premium
```

### Code example

```typescript
export class MemberComponent {

  memberName = 'John';
  age = 30;

}
```

```html
<h2>{{ memberName }}</h2>
<p>Age: {{ age }}</p>
```

### Interview answer

> **Interpolation is an Angular template syntax used to display component data in the HTML using double curly braces. It is mainly used for one-way data flow from the component to the template.**

### Common mistake

❌ Saying interpolation can be used for everything.

For example:

```html
<button disabled="{{ isDisabled }}">
```

Although Angular can evaluate interpolation in many attributes, **property binding is the clearer and preferred approach for DOM properties**:

```html
<button [disabled]="isDisabled">
```

---

# 2. What is Property Binding?

### What is it?

**Property binding** allows us to bind a component value to a DOM element property or Angular component property.

Syntax:

```html
[property]="expression"
```

Data flows:

```text
Component
    ↓
Template
```

### Why do we use it?

We use property binding when a value needs to dynamically control an element.

Examples:

- Disable a button
- Set an image source
- Set input value
- Control visibility/state
- Pass data to a child component

### Real project example

Suppose a Save button should be disabled while an API request is running.

```typescript
isSaving = true;
```

Template:

```html
<button [disabled]="isSaving">
    Save Member
</button>
```

When:

```text
isSaving = true
```

the button becomes disabled.

### Code example

```typescript
isDisabled = true;
imageUrl = 'assets/member.png';
```

```html
<button [disabled]="isDisabled">
    Save
</button>

<img [src]="imageUrl">
```

### Interview answer

> **Property binding is used to dynamically set a DOM element or Angular component property using a value from the component. It provides one-way data flow from the component to the template.**

### Common mistake

Don't confuse:

```html
[disabled]="isDisabled"
```

with:

```html
disabled="isDisabled"
```

The second one is treated as a literal attribute value rather than Angular property binding.

---

# 3. What is Event Binding?

### What is it?

**Event binding** allows Angular to listen to events from the template and execute component logic.

Syntax:

```html
(event)="method()"
```

Data/event flow:

```text
Template
    ↓
Component
```

### Why do we use it?

We use event binding to respond to user actions such as:

- Click
- Input
- Change
- Submit
- Key press
- Mouse events

### Real project example

When the user clicks the Delete button:

```html
<button (click)="deleteMember()">
    Delete
</button>
```

Angular calls:

```typescript
deleteMember() {
    // Delete member logic
}
```

### Code example

```typescript
deleteMember() {
    console.log('Member deleted');
}
```

```html
<button (click)="deleteMember()">
    Delete
</button>
```

You can also access the event:

```html
<input (input)="onInput($event)">
```

```typescript
onInput(event: Event) {
    const value = (event.target as HTMLInputElement).value;
    console.log(value);
}
```

### Interview answer

> **Event binding allows the Angular template to communicate user or DOM events to the component. It is represented using parentheses and is commonly used for events such as click, input, change, and submit.**

### Common mistake

❌ Thinking `(click)` is a function.

It is **event binding** that tells Angular which component method should execute when the click event occurs.

---

# 4. What is Two-Way Data Binding?

### What is it?

Two-way data binding means that data can flow in both directions:

```text
Component
    ↕
Template
```

A common Angular syntax is:

```html
[(ngModel)]
```

This is often called **banana-in-a-box syntax**.

### Why do we use it?

It is useful when the UI and component property need to stay synchronized.

Common example:

- Forms
- Search fields
- Editable values
- User input

### Real project example

Suppose we have an edit-member screen.

```typescript
memberName = 'John';
```

Template:

```html
<input [(ngModel)]="memberName">

<p>{{ memberName }}</p>
```

If the user changes:

```text
John → Jahanvi
```

the component's `memberName` is also updated.

### Code example

```typescript
memberName = '';
```

```html
<input [(ngModel)]="memberName">

<p>Hello {{ memberName }}</p>
```

### Interview answer

> **Two-way data binding synchronizes a value between the component and the template. When the component value changes, the UI updates, and when the user changes the UI value, the component value is updated. In template-driven forms, [(ngModel)] is commonly used for this.**

### Common mistake

Don't say:

> Angular always uses two-way binding.

Angular supports multiple binding patterns. One-way binding is often preferred where possible because it makes data flow easier to understand.

---

# 5. What is ngModel?

### What is it?

`ngModel` is an Angular directive commonly used for **two-way data binding** in template-driven forms.

Syntax:

```html
[(ngModel)]="property"
```

### Why do we use it?

`ngModel` helps synchronize form controls with component properties.

It can also participate in Angular's template-driven form features such as validation and form state.

### Real project example

Member registration form:

```html
<input
  type="text"
  [(ngModel)]="member.name">
```

Component:

```typescript
member = {
    name: ''
};
```

When the user types a name, `member.name` is updated.

### Code example

```typescript
memberName = '';
```

```html
<label>Member Name</label>

<input
  type="text"
  [(ngModel)]="memberName">

<p>Entered: {{ memberName }}</p>
```

### Interview answer

> **ngModel is an Angular directive used primarily in template-driven forms to bind form controls to component properties. When used with [(ngModel)], it provides two-way data binding.**

### Common mistake

❌ Saying:

> `ngModel` is only for two-way binding.

It can also be used as:

```html
[ngModel]="memberName"
```

or:

```html
(ngModelChange)="onNameChange($event)"
```

But `[(ngModel)]` combines the two.

---

# 6. What is a Directive?

### What is it?

A **directive** is a class that allows us to add behavior to DOM elements or change how Angular handles them.

Angular directives can be used to:

- Change the appearance of an element.
- Change element behavior.
- Dynamically create/remove elements.
- Respond to changes.
- Reuse DOM-related behavior.

### Why do we use it?

Directives allow us to add reusable behavior to HTML elements without creating a complete component.

### Real project example

Suppose inactive members should appear differently.

We can use:

```html
<div [ngClass]="{'inactive': !member.isActive}">
    {{ member.name }}
</div>
```

Here `ngClass` changes the CSS classes based on the member's state.

### Code example

```html
<p *ngIf="isLoggedIn">
    Welcome back!
</p>
```

Here `ngIf` controls whether the element exists in the rendered view.

### Interview answer

> **A directive is a class that adds behavior or changes the structure or appearance of DOM elements. Angular provides built-in directives such as ngClass and ngStyle, and developers can also create custom directives.**

### Common mistake

❌ Saying:

> Every directive is a component.

A component is a specialized Angular construct with a template. A directive generally attaches behavior to an existing element.

---

# 7. Difference Between Structural and Attribute Directives

### What is it?

Angular directives are commonly discussed as:

```text
Structural Directives
Attribute Directives
```

### Why do we use it?

The key difference is **what they change**.

### Structural Directive

A structural directive changes the **structure of the DOM/view**.

Examples in traditional Angular syntax:

```text
*ngIf
*ngFor
```

They can add/remove/repeat views.

### Attribute Directive

An attribute directive changes the **appearance or behavior** of an existing element.

Examples:

```text
ngClass
ngStyle
```

### Real project example

#### Structural

Show member only when active:

```html
<div *ngIf="member.isActive">
    {{ member.name }}
</div>
```

The view is conditionally created.

#### Attribute

Change the class:

```html
<div [ngClass]="{
    'active': member.isActive,
    'inactive': !member.isActive
}">
    {{ member.name }}
</div>
```

The element remains, but its styling changes.

### Code example

| Type       | Purpose                     | Examples             |
| ---------- | --------------------------- | -------------------- |
| Structural | Changes DOM/view structure  | `*ngIf`, `*ngFor`    |
| Attribute  | Changes appearance/behavior | `ngClass`, `ngStyle` |

### Interview answer

> \*\*Structural directives change the structure of the rendered view by adding, removing, or repeating elements. Attribute directives modify the behavior or appearance of an existing element. Traditional examples are *ngIf and *ngFor for structural behavior, and ngClass and ngStyle for attribute behavior.**

### Common mistake

❌ Saying structural directives only hide elements.

For example, `*ngFor` doesn't simply hide elements; it **creates multiple views based on a collection**.

---

# 8. What is \*ngIf?

### What is it?

`*ngIf` is the traditional Angular structural directive used to conditionally render a template.

Example:

```html
<div *ngIf="isLoggedIn">
    Welcome!
</div>
```

If:

```typescript
isLoggedIn = true;
```

the content is rendered.

If:

```typescript
isLoggedIn = false;
```

the view is not rendered.

### Why do we use it?

Common uses:

- Show/hide sections.
- Display loading messages.
- Show error messages.
- Display content based on permissions.
- Show buttons based on user roles.

### Real project example

Display an Edit button only when the member is active:

```html
<button *ngIf="member.isActive">
    Edit
</button>
```

### Code example

```typescript
isLoading = true;
```

```html
<div *ngIf="isLoading">
    Loading members...
</div>
```

### Interview answer

> \**Traditionally, *ngIf is a structural directive used to conditionally add or remove a view from the rendered DOM based on an expression. In modern Angular, the equivalent built-in control-flow syntax is @if.**

### Common mistake

Don't say:

> `*ngIf` just changes CSS display to none.

It is fundamentally about **conditional view rendering**, not simply setting CSS.

---

# 9. What is \*ngFor?

### What is it?

`*ngFor` is the traditional Angular structural directive used to iterate over a collection and create a view for each item.

### Why do we use it?

We use it to display lists such as:

- Members
- Products
- Orders
- Employees
- Transactions

### Real project example

Suppose the API returns:

```typescript
members = [
    { id: 1, name: 'John' },
    { id: 2, name: 'David' },
    { id: 3, name: 'Sarah' }
];
```

Template:

```html
<div *ngFor="let member of members">
    {{ member.name }}
</div>
```

Output:

```text
John
David
Sarah
```

### Code example

```html
<ul>
    <li *ngFor="let member of members">
        {{ member.name }}
    </li>
</ul>
```

In older Angular versions, you may also see:

```html
*ngFor="let member of members; index as i"
```

### Interview answer

> \**Traditionally, *ngFor is a structural directive used to iterate over a collection and create a template instance for each item. In modern Angular, @for is the newer built-in control-flow syntax.**

### Common mistake

❌ Using `*ngFor` without considering performance for large lists.

For large collections, Angular's modern `@for` syntax and appropriate tracking can help Angular efficiently identify which items changed.

---

# 10. What is ngClass?

### What is it?

`ngClass` is an Angular attribute directive used to dynamically add or remove CSS classes.

### Why do we use it?

It is useful when styling depends on application state.

Examples:

- Active/inactive
- Success/error
- Selected/unselected
- Valid/invalid

### Real project example

```typescript
member.isActive = true;
```

```html
<div
  [ngClass]="{
    'active-member': member.isActive,
    'inactive-member': !member.isActive
  }">
    {{ member.name }}
</div>
```

### Code example

```html
<div [ngClass]="currentClass">
    Member
</div>
```

Component:

```typescript
currentClass = 'active-member';
```

### Interview answer

> **ngClass is an Angular attribute directive used to dynamically add or remove CSS classes based on component data or conditions.**

### Common mistake

For a single simple class, `[class.someClass]` may be simpler:

```html
<div [class.active]="member.isActive">
```

Use `ngClass` when you need more dynamic class handling.

---

# 11. What is ngStyle?

### What is it?

`ngStyle` is an Angular attribute directive used to dynamically set inline CSS styles.

### Why do we use it?

We use it when styling depends dynamically on component data.

### Real project example

Display membership status with different styling:

```html
<div
  [ngStyle]="{
    'font-size.px': fontSize,
    'font-weight': 'bold'
  }">
    Premium Member
</div>
```

### Code example

```typescript
fontSize = 18;
```

```html
<p [ngStyle]="{
    'font-size.px': fontSize
}">
    Member Details
</p>
```

### Interview answer

> **ngStyle is an Angular attribute directive used to dynamically apply inline styles based on component properties or expressions.**

### Common mistake

Don't use `ngStyle` for every styling requirement.

For static styling, normal CSS classes are generally cleaner:

```html
<div class="member-card">
```

Use dynamic class/style binding when the value actually depends on application state.

---

# 12. What is a Pipe?

### What is it?

A **pipe** transforms data in an Angular template for display without changing the original component data.

Syntax:

```html
{{ value | pipeName }}
```

Angular provides built-in pipes such as:

```text
date
currency
uppercase
lowercase
number
percent
json
```

### Why do we use it?

Pipes are useful for presentation formatting.

For example:

```text
2026-10-06
```

can be displayed as:

```text
06/10/2026
```

### Real project example

Display membership registration date:

```html
<p>
    Joined: {{ member.joinedDate | date:'dd/MM/yyyy' }}
</p>
```

Display membership fee:

```html
<p>
    Fee: {{ member.fee | currency:'INR' }}
</p>
```

### Code example

```html
<p>{{ member.name | uppercase }}</p>

<p>{{ member.joinedDate | date:'dd/MM/yyyy' }}</p>

<p>{{ member.fee | currency:'INR' }}</p>
```

### Interview answer

> **A pipe transforms data for presentation in an Angular template. Angular provides built-in pipes such as date, currency, uppercase, and number, and we can also create custom pipes for application-specific transformations.**

### Common mistake

❌ Using pipes for complex business logic.

Pipes should generally focus on **presentation transformation**, not major business operations.

---

# 13. What is a Custom Pipe?

### What is it?

A **custom pipe** is a pipe created by the developer for application-specific data transformation.

We create one using the `@Pipe` decorator.

### Why do we use it?

When Angular's built-in pipes don't meet our requirement, we can create our own.

### Real project example

Suppose our application stores membership status as:

```text
A
I
```

But the UI should display:

```text
Active
Inactive
```

A custom pipe can handle this transformation.

### Code example

```typescript
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'membershipStatus'
})
export class MembershipStatusPipe implements PipeTransform {

  transform(status: string): string {
    return status === 'A' ? 'Active' : 'Inactive';
  }

}
```

Template:

```html
<p>
    Status: {{ member.status | membershipStatus }}
</p>
```

### Interview answer

> **A custom pipe is a developer-created pipe used to perform application-specific presentation transformations that are not provided by Angular's built-in pipes.**

### Common mistake

Don't put complex business logic or API calls inside a pipe.

A pipe should generally remain focused on transforming data for display.

---

# 14. What is a Pure vs Impure Pipe?

### What is it?

Angular pipes are **pure by default**.

The difference is related to **when Angular executes the pipe**.

### Pure Pipe

A pure pipe runs when Angular detects a change to the pipe's input value or its input arguments.

Example:

```typescript
@Pipe({
  name: 'membershipStatus',
  pure: true
})
```

Pure pipes are generally more efficient because Angular doesn't need to execute them on every change-detection cycle.

### Impure Pipe

An impure pipe is declared with:

```typescript
@Pipe({
  name: 'myPipe',
  pure: false
})
```

Angular may execute it during every change-detection cycle.

### Why do we use them?

Pure pipes are preferred for most transformations because they provide better performance and predictable behavior.

Impure pipes are useful when the output needs to respond to changes that Angular's normal pure-pipe input checking would not detect, such as certain in-place mutations.

### Real project example

Suppose we have:

```typescript
members = [
    { name: 'John' },
    { name: 'David' }
];
```

A pure pipe works well when a new array reference is supplied:

```typescript
this.members = [...this.members, newMember];
```

However, if we mutate the existing array:

```typescript
this.members.push(newMember);
```

the array reference remains the same.

This is one reason understanding **immutability/reference changes** matters when working with pure pipes.

### Code example

Pure:

```typescript
@Pipe({
  name: 'uppercaseName',
  pure: true
})
export class UppercaseNamePipe implements PipeTransform {

  transform(name: string): string {
    return name.toUpperCase();
  }

}
```

Impure:

```typescript
@Pipe({
  name: 'memberFilter',
  pure: false
})
export class MemberFilterPipe implements PipeTransform {

  transform(members: any[], search: string): any[] {
    return members.filter(x =>
      x.name.toLowerCase().includes(search.toLowerCase())
    );
  }

}
```

### Interview answer

> **Angular pipes are pure by default. A pure pipe is evaluated when its input value or arguments change, while an impure pipe can be evaluated during every change-detection cycle. Pure pipes are generally preferred for performance, and impure pipes should be used carefully.**

### Common mistake

❌ Saying:

> Pure pipes run only once.

They don't necessarily run only once. They run when Angular determines their input or arguments have changed.

---

# 15. What is Dependency Injection in Angular?

### What is it?

**Dependency Injection (DI)** is a design pattern where a class receives the objects/services it depends on instead of creating them itself.

Without DI:

```typescript
export class MemberComponent {

  service = new MemberService();

}
```

With DI:

```typescript
export class MemberComponent {

  constructor(private memberService: MemberService) {}

}
```

Angular's DI system provides the required dependency.

### Why do we use it?

DI provides:

- Loose coupling
- Reusability
- Testability
- Centralized dependency management
- Easier maintenance

### Real project example

A component should not directly create an API service.

Instead:

```text
MemberComponent
      ↓
MemberService
      ↓
HttpClient
      ↓
.NET API
```

Angular injects `MemberService` into `MemberComponent`.

### Code example

Service:

```typescript
@Injectable({
  providedIn: 'root'
})
export class MemberService {

  getMembers() {
    // API call
  }

}
```

Component:

```typescript
export class MemberComponent {

  constructor(
    private memberService: MemberService
  ) {}

}
```

Angular creates/provides the service according to its DI configuration.

### Interview answer

> **Dependency Injection is a design pattern used by Angular to provide a class with its required dependencies rather than having the class create them directly. Angular has a built-in hierarchical DI system, which improves loose coupling, reusability, maintainability, and testability.**

### Common mistake

❌ Saying:

> DI means creating an object inside the constructor.

The important concept is that **the dependency is provided by Angular's DI system**, rather than manually creating it with `new`.

---

# 16. What is a Service in Angular?

### What is it?

A **service** is a TypeScript class used to encapsulate reusable application logic or functionality.

Services commonly handle:

- API calls
- Business-related client logic
- Shared data
- Authentication
- Logging
- State-related functionality

### Why do we use it?

Services help keep components focused on UI responsibilities.

Instead of putting API calls directly inside a component:

```text
Component
    ↓
Service
    ↓
HTTP API
```

### Real project example

For a membership application:

```text
MemberComponent
       ↓
MemberService
       ↓
HttpClient
       ↓
.NET Web API
       ↓
MySQL
```

`MemberService` can contain methods such as:

```typescript
getMembers()
getMemberById()
addMember()
updateMember()
deleteMember()
```

### Code example

```typescript
@Injectable({
  providedIn: 'root'
})
export class MemberService {

  constructor(private http: HttpClient) {}

  getMembers() {
    return this.http.get('/api/members');
  }

  deleteMember(id: number) {
    return this.http.delete(`/api/members/${id}`);
  }

}
```

Component:

```typescript
export class MemberComponent {

  constructor(
    private memberService: MemberService
  ) {}

  loadMembers() {
    this.memberService.getMembers()
      .subscribe(data => {
        console.log(data);
      });
  }

}
```

### Interview answer

> **An Angular service is a reusable class that encapsulates functionality that should be shared or separated from component UI logic. A common use case is placing HTTP/API communication in services and injecting those services into components using Angular's dependency injection system.**

### Common mistake

❌ Saying:

> Every service must call an API.

Services don't have to call APIs. They can contain authentication logic, shared state, logging, calculations, or other reusable functionality.

---

# 17. What is the @Injectable Decorator?

### What is it?

`@Injectable` is a decorator that tells Angular that a class participates in Angular's dependency injection system.

It is commonly used on services.

Example:

```typescript
@Injectable({
  providedIn: 'root'
})
export class MemberService {

}
```

### Why do we use it?

It allows Angular to understand how the class should participate in dependency injection and what dependencies it may need.

For example:

```typescript
@Injectable({
  providedIn: 'root'
})
export class MemberService {

  constructor(private http: HttpClient) {}

}
```

Angular can resolve `HttpClient` and inject it into the service.

### Real project example

A member service depends on `HttpClient`:

```text
MemberComponent
       ↓
MemberService
       ↓
HttpClient
```

Angular's DI system resolves these dependencies.

### Code example

```typescript
@Injectable({
  providedIn: 'root'
})
export class MemberService {

  constructor(
    private http: HttpClient
  ) {}

}
```

### Interview answer

> **@Injectable is an Angular decorator that marks a class as available for dependency injection and provides metadata Angular can use to resolve its dependencies. It is commonly used with services.**

### Common mistake

❌ Saying:

> `@Injectable` means the class is automatically a singleton.

That is not the complete explanation.

The lifetime/scope depends on **where the provider is registered**.

---

# 18. What is providedIn: 'root'?

### What is it?

When we write:

```typescript
@Injectable({
  providedIn: 'root'
})
```

we are telling Angular to provide the service through the **root injector**.

For the usual application setup, this means the service is available throughout the application and typically behaves as a **singleton instance within that application's injector**.

### Why do we use it?

Benefits include:

- Application-wide availability.
- No need to manually register the service in a module's `providers` in the common case.
- Tree-shakable provider configuration.
- Clear service scope.

### Real project example

For an application-wide authentication service:

```typescript
@Injectable({
  providedIn: 'root'
})
export class AuthService {

  isLoggedIn = false;

}
```

Different components can inject the service:

```text
LoginComponent
       ↓
   AuthService
       ↑
       |
DashboardComponent
```

They can access the same root-provided service instance in the normal root-injector scenario.

### Code example

```typescript
@Injectable({
  providedIn: 'root'
})
export class MemberService {

}
```

Then:

```typescript
export class MemberComponent {

  constructor(
    private memberService: MemberService
  ) {}

}
```

No manual module provider registration is needed for this root-provided service.

### Interview answer

> **providedIn: 'root' registers the service with Angular's root injector. This makes the service available throughout the application and, under the root injector, normally results in one shared service instance for the application. It also supports tree-shakable provider configuration.**

### Common mistake

❌ Saying:

> `providedIn: 'root'` means the service is always globally available in every Angular context.

More precisely, it registers the service with the **root injector**. Angular has a **hierarchical dependency injection system**, so a component or feature can also have a more local provider that creates a different instance within that injector scope.

---

# ⭐ Important Interview Connection

These concepts are strongly connected:

```text
Component
    ↓
Needs MemberService
    ↓
Dependency Injection
    ↓
@Injectable
    ↓
providedIn: 'root'
    ↓
Angular Root Injector
```

And:

```text
Component
    ↓
Template
    ↓
Data Binding
    ├── Interpolation
    ├── Property Binding
    ├── Event Binding
    └── Two-Way Binding
```

And:

```text
Template
    ↓
Directives
    ├── Structural
    │     ├── *ngIf
    │     └── *ngFor
    │
    └── Attribute
          ├── ngClass
          └── ngStyle
```

And:

```text
Template
    ↓
Pipe
    ↓
Display Transformation
```

---

# ⭐ 4-Year Experience Scenario

### Interviewer:

> Your MemberComponent currently contains 500 lines of code. It makes HTTP calls, handles UI events, performs formatting, and contains authentication logic. What would you change?

### Good answer:

> I would separate responsibilities. The component should primarily handle UI-related state and interactions. I would move API communication into services, use Angular's dependency injection to inject those services, use pipes for presentation formatting, and use appropriate reusable components/directives where required. Authentication-related functionality can be handled through a dedicated authentication service and, where appropriate, HTTP interceptors or route guards.

Architecture:

```text
MemberComponent
       │
       ├── UI state
       ├── User interactions
       │
       ↓
MemberService
       │
       ↓
HttpClient
       │
       ↓
.NET Web API
```

This improves:

- Maintainability
- Testability
- Reusability
- Separation of concerns
- Readability

---

# ⭐ Quick Revision Table

| Concept              | Main Purpose                         | Example                     |
| -------------------- | ------------------------------------ | --------------------------- |
| Interpolation        | Display component data               | `{{ name }}`                |
| Property Binding     | Component → UI property              | `[disabled]="isSaving"`     |
| Event Binding        | UI event → component                 | `(click)="save()"`          |
| Two-Way Binding      | Component ↔ UI                       | `[(ngModel)]="name"`        |
| `ngModel`            | Form control binding                 | `[(ngModel)]="name"`        |
| Directive            | Add behavior/structure               | `ngClass`                   |
| Structural Directive | Change view structure                | `*ngIf`, `*ngFor`           |
| Attribute Directive  | Change behavior/style                | `ngClass`, `ngStyle`        |
| `*ngIf`              | Conditional view                     | `*ngIf="isActive"`          |
| `*ngFor`             | Iterate collection                   | `*ngFor="let m of members"` |
| `ngClass`            | Dynamic CSS classes                  | `[ngClass]="classes"`       |
| `ngStyle`            | Dynamic inline styles                | `[ngStyle]="styles"`        |
| Pipe                 | Transform display data               | `{{ date \| date }}`        |
| Custom Pipe          | Custom transformation                | `membershipStatus`          |
| Pure Pipe            | Runs based on input/args changes     | Default                     |
| Impure Pipe          | Can run every change detection cycle | `pure: false`               |
| DI                   | Provides dependencies                | Inject `MemberService`      |
| Service              | Reusable application logic           | `MemberService`             |
| `@Injectable`        | DI metadata                          | `@Injectable()`             |
| `providedIn: 'root'` | Root injector registration           | Application-wide service    |

---

# ⭐ One-Line Interview Revision

```text
Interpolation     → Display data
Property Binding  → Set properties
Event Binding     → Handle events
Two-Way Binding   → Synchronize UI + component
ngModel            → Form control binding
Directive          → Add behavior/structure
*ngIf              → Conditional rendering
*ngFor             → List rendering
ngClass            → Dynamic classes
ngStyle            → Dynamic styles
Pipe               → Transform display data
Custom Pipe        → Custom transformation
Pure Pipe          → Input/reference-based execution
Impure Pipe        → Frequent change detection execution
DI                 → Provide dependencies
Service            → Reusable logic
@Injectable         → DI metadata
providedIn: root   → Root injector provider
```

---

# ⚠️ Modern Angular Interview Note

For a **4-year Angular interview**, don't study only the older syntax.

You should recognize both:

### Traditional syntax

```html
<div *ngIf="isActive">
    Active
</div>

<div *ngFor="let member of members">
    {{ member.name }}
</div>
```

### Modern Angular control flow

```html
@if (isActive) {
    <div>Active</div>
}

@for (member of members; track member.id) {
    <div>{{ member.name }}</div>
}
```

Similarly, understand that modern Angular supports **standalone components**, so `NgModule` and `AppModule` are important concepts to understand, but they are no longer mandatory for every Angular application.

For your interviews, be comfortable explaining **why a project uses either approach** rather than simply memorizing syntax.



# Angular Routing, Lifecycle, Component Communication & Change Detection

> **Target:** 4 Years Experience
> **Focus:** Interview + Real Project Understanding
> **Stack:** Angular + .NET Web API

---

# 1. What is Hierarchical Dependency Injection?

### What is it?

Angular uses a **hierarchical Dependency Injection (DI) system**, meaning dependencies can be provided at different levels of the application.

A simplified hierarchy is:

```text
Root Injector
     ↓
Environment / Application
     ↓
Component Injector
     ↓
Child Component Injector
```

Angular looks for a requested dependency starting from the current injector and can move upward through the hierarchy to find a provider.

### Why do we use it?

Hierarchical DI allows us to control the **scope and lifetime of a service**.

For example:

- Application-wide service → root level
- Feature-specific service → feature/application scope
- Component-specific service → component level
- Child component can inherit a parent-provided service

This is particularly important when we need **different instances of the same service**.

### Real project example

Suppose `MemberService` is provided at root:

```typescript
@Injectable({
  providedIn: 'root'
})
export class MemberService {
}
```

Multiple components normally receive the same root-provided instance.

But if we provide it at a component:

```typescript
@Component({
  selector: 'app-member',
  providers: [MemberService]
})
export class MemberComponent {
}
```

Angular creates a service instance associated with that component's injector.

A child component can inherit that instance unless it provides its own instance.

### Code example

```typescript
@Component({
  selector: 'app-member',
  providers: [MemberService],
  templateUrl: './member.component.html'
})
export class MemberComponent {

  constructor(private memberService: MemberService) {}

}
```

### Interview answer

> **Angular uses hierarchical dependency injection, where providers can exist at different levels such as the root or component level. Angular resolves a dependency through the injector hierarchy, which allows us to control the scope and instances of services.**

### Common mistake

❌ Saying:

> `providedIn: 'root'` is the only way Angular provides services.

Services can also be provided at more local levels, such as a component or route.

---

# 2. What is Angular Router?

### What is it?

The **Angular Router** is Angular's built-in routing system used to navigate between different views/components in a single-page application.

It maps a URL to a component.

For example:

```text
/members
     ↓
MemberListComponent

/members/101
     ↓
MemberDetailsComponent

/login
     ↓
LoginComponent
```

### Why do we use it?

We use Angular Router to:

- Navigate between pages.
- Create application URLs.
- Pass route parameters.
- Protect routes.
- Lazy-load features.
- Handle nested routes.
- Read query parameters.

### Real project example

A Membership Management application could have:

```text
/login
/dashboard
/members
/members/101
/members/add
/reports
```

### Code example

```typescript
const routes: Routes = [
  {
    path: 'members',
    component: MemberListComponent
  },
  {
    path: 'members/:id',
    component: MemberDetailsComponent
  }
];
```

### Interview answer

> **Angular Router is the built-in routing mechanism used to map application URLs to components and manage navigation in a single-page application without performing a full browser page reload.**

### Common mistake

❌ Saying Angular Router calls the backend API.

Routing controls **frontend navigation**. Services/HttpClient are responsible for API communication.

---

# 3. What is a Route Guard?

### What is it?

A **route guard** controls whether navigation to or from a route should be allowed.

It is commonly used for:

- Authentication
- Authorization
- Unsaved form changes
- Permission checks

### Why do we use it?

Suppose an unauthenticated user tries to access:

```text
/reports
```

The application can check whether the user is authenticated.

```text
User
 ↓
/reports
 ↓
Auth Guard
 ↓
Authenticated?
 ├── Yes → Reports
 └── No  → Login
```

### Real project example

Only logged-in users should access the Member Management screen.

```typescript
canActivate: [authGuard]
```

The guard checks whether the user has a valid authentication state/token before allowing navigation.

### Code example

Modern functional guard:

```typescript
export const authGuard: CanActivateFn = () => {

  const authService = inject(AuthService);
  const router = inject(Router);

  if (authService.isLoggedIn()) {
    return true;
  }

  return router.createUrlTree(['/login']);
};
```

Route:

```typescript
{
  path: 'members',
  component: MemberListComponent,
  canActivate: [authGuard]
}
```

### Interview answer

> **A route guard controls whether navigation to or from a route is allowed. It is commonly used for authentication, authorization, unsaved changes, and other navigation-related checks.**

### Common mistake

❌ Saying:

> Route guards provide complete backend security.

They are a **frontend navigation control**. Backend APIs must still enforce authentication and authorization.

---

# 4. Types of Route Guards

### What is it?

Angular provides different guard interfaces/functions for different navigation scenarios.

Important ones include:

```text
CanActivate
CanActivateChild
CanDeactivate
CanMatch
```

You may also encounter:

```text
CanLoad
```

in older Angular applications.

### Why do we use it?

Different guards solve different problems.

| Guard              | Purpose                               |
| ------------------ | ------------------------------------- |
| `CanActivate`      | Can the user enter a route?           |
| `CanActivateChild` | Can the user enter child routes?      |
| `CanDeactivate`    | Can the user leave a route?           |
| `CanMatch`         | Should a route be considered/matched? |
| `CanLoad`          | Older lazy-loading guard              |

### Real project example

#### CanActivate

Protect `/admin`.

```text
User → /admin → Auth check → Allow/Deny
```

#### CanDeactivate

User edits a member:

```text
Edit Member
     ↓
Changes not saved
     ↓
User clicks another page
     ↓
"Are you sure?"
```

### Code example

```typescript
{
  path: 'edit-member',
  component: EditMemberComponent,
  canDeactivate: [unsavedChangesGuard]
}
```

### Interview answer

> **CanActivate controls access to a route, CanActivateChild controls access to child routes, CanDeactivate controls whether a user can leave a route, and CanMatch controls whether a route can be matched. In older Angular applications, CanLoad may also be seen for lazy-loaded modules.**

### Common mistake

Don't confuse:

```text
CanActivate → Enter route
CanDeactivate → Leave route
```

---

# 5. What is Lazy Loading in Angular?

### What is it?

**Lazy loading** means loading a feature only when it is required instead of loading the entire feature when the application initially starts.

Without lazy loading:

```text
Application starts
     ↓
Load everything
     ↓
Display application
```

With lazy loading:

```text
Application starts
     ↓
Load required code
     ↓
User opens Reports
     ↓
Load Reports feature
```

### Why do we use it?

Lazy loading can:

- Reduce initial JavaScript bundle size.
- Improve initial application startup.
- Improve performance for large applications.
- Separate large application features.

### Real project example

Suppose our application contains:

```text
Dashboard
Members
Reports
Admin
```

The Reports section may be large and not used by every user.

We can lazy-load it only when the user navigates to:

```text
/reports
```

### Code example

Modern standalone route:

```typescript
{
  path: 'reports',
  loadComponent: () =>
    import('./reports/reports.component')
      .then(m => m.ReportsComponent)
}
```

A lazy-loaded route can also load a group of routes:

```typescript
{
  path: 'members',
  loadChildren: () =>
    import('./members/member.routes')
      .then(m => m.MEMBER_ROUTES)
}
```

### Interview answer

> **Lazy loading is a technique where Angular loads a feature's code only when the user navigates to that feature instead of loading everything during the initial application startup. It helps reduce the initial bundle and can improve startup performance.**

### Common mistake

❌ Saying:

> Lazy loading means loading data from the API later.

Lazy loading primarily refers to **loading application code/features on demand**.

---

# 6. What is a Route Resolver?

### What is it?

A **route resolver** allows Angular to retrieve required data before a route is activated.

The route waits for the resolver's result before completing navigation.

### Why do we use it?

It is useful when a page cannot be meaningfully displayed until required data is available.

For example:

```text
Navigate to /members/101
          ↓
Resolver
          ↓
Get Member 101
          ↓
Route activated
          ↓
MemberDetailsComponent
```

### Real project example

When opening:

```text
/members/101
```

we may want the member details to be available immediately when the component loads.

### Code example

```typescript
export const memberResolver: ResolveFn<Member> = (route) => {

  const service = inject(MemberService);
  const id = Number(route.paramMap.get('id'));

  return service.getMemberById(id);
};
```

Route:

```typescript
{
  path: 'members/:id',
  component: MemberDetailsComponent,
  resolve: {
    member: memberResolver
  }
}
```

The component can access the resolved data through route data.

### Interview answer

> **A route resolver retrieves required data before a route is activated. It is useful when the component needs data available at the time navigation completes, such as loading member details before displaying the member details page.**

### Common mistake

❌ Saying:

> Resolver is required for every API call.

It is optional. Many applications simply load data inside the component/service.

---

# 7. What is RouterOutlet?

### What is it?

`RouterOutlet` is a directive that acts as a **placeholder where Angular renders the component associated with the current route**.

### Why do we use it?

It provides the location where routed components should appear.

### Real project example

Suppose `app.component.html` contains:

```html
<app-header></app-header>

<router-outlet></router-outlet>

<app-footer></app-footer>
```

When the URL is:

```text
/members
```

Angular renders:

```text
MemberListComponent
```

inside:

```html
<router-outlet>
```

### Code example

```html
<header>
    Membership Management
</header>

<router-outlet></router-outlet>
```

### Interview answer

> **RouterOutlet is a directive that acts as a placeholder in the application template where Angular renders the component associated with the currently activated route.**

### Common mistake

❌ Thinking `router-outlet` is a component.

It is a directive provided by Angular Router.

---

# 8. What is RouterLink?

### What is it?

`RouterLink` is an Angular directive used to navigate between routes from the template.

### Why do we use it?

It allows navigation without manually manipulating the browser URL.

### Real project example

```html
<a routerLink="/members">
    Members
</a>
```

When the user clicks it, Angular navigates to:

```text
/members
```

without performing a full browser page reload.

### Code example

```html
<a routerLink="/dashboard">
    Dashboard
</a>

<a routerLink="/members">
    Members
</a>
```

Route parameters:

```html
<a [routerLink]="['/members', member.id]">
    View Member
</a>
```

### Interview answer

> **RouterLink is an Angular directive used in templates to navigate to application routes. It works with Angular Router and enables SPA navigation without a full page reload.**

### Common mistake

Don't confuse:

```html
routerLink="/members"
```

with:

```typescript
this.router.navigate(['/members']);
```

`routerLink` is commonly used in templates, while `Router.navigate()` is commonly used from TypeScript code.

---

# 9. What is ActivatedRoute?

### What is it?

`ActivatedRoute` provides information about the **currently activated route**.

It can be used to access:

- Route parameters
- Query parameters
- Route data
- Resolved data
- Parent/child route information

### Why do we use it?

Suppose the URL is:

```text
/members/101
```

We need to retrieve:

```text
101
```

from the route.

### Real project example

Route:

```typescript
{
  path: 'members/:id',
  component: MemberDetailsComponent
}
```

Component:

```typescript
constructor(private route: ActivatedRoute) {}

ngOnInit() {
  const id = this.route.snapshot.paramMap.get('id');
}
```

### Code example

For a reactive approach:

```typescript
this.route.paramMap.subscribe(params => {
  const id = params.get('id');
});
```

For query parameters:

```text
/members?page=2
```

```typescript
this.route.queryParamMap.subscribe(params => {
  const page = params.get('page');
});
```

### Interview answer

> **ActivatedRoute provides information about the currently activated route, including route parameters, query parameters, route data, and resolved data. It is commonly used when a component needs information from the URL.**

### Common mistake

Don't confuse:

```text
ActivatedRoute → Read current route information
Router → Navigate/change routes
```

---

# 10. What are Angular Lifecycle Hooks?

### What is it?

Angular lifecycle hooks are methods that allow a component or directive to execute code at specific stages of its lifecycle.

Simplified lifecycle:

```text
Create
  ↓
Input changes
  ↓
Initialization
  ↓
View initialization
  ↓
Changes
  ↓
Destroy
```

Common hooks include:

```text
ngOnChanges
ngOnInit
ngDoCheck
ngAfterContentInit
ngAfterContentChecked
ngAfterViewInit
ngAfterViewChecked
ngOnDestroy
```

### Why do we use it?

Lifecycle hooks allow us to perform actions at the appropriate stage.

Examples:

- Initialize data
- Respond to input changes
- Access child views
- Clean up subscriptions
- Release resources

### Real project example

A member component may:

```text
ngOnInit
   ↓
Load member data

ngAfterViewInit
   ↓
Access a ViewChild

ngOnDestroy
   ↓
Cleanup subscriptions/resources
```

### Interview answer

> **Angular lifecycle hooks are methods that allow us to execute code at specific stages in the lifecycle of a component or directive, such as initialization, input changes, view initialization, and destruction.**

### Common mistake

❌ Putting every piece of logic inside `ngOnInit`.

Each hook has a specific purpose.

---

# 11. Explain ngOnInit

### What is it?

`ngOnInit` is called after Angular has initialized the component's input properties.

It is commonly used for **initialization logic**.

### Why do we use it?

Typical uses include:

- Initial API calls
- Initializing component data
- Setting up initial state
- Reading initial route information

### Real project example

When the Member List page loads:

```text
Component created
      ↓
ngOnInit()
      ↓
Call MemberService
      ↓
Get members
      ↓
Display members
```

### Code example

```typescript
export class MemberListComponent
  implements OnInit {

  members: Member[] = [];

  constructor(
    private memberService: MemberService
  ) {}

  ngOnInit(): void {

    this.memberService.getMembers()
      .subscribe(data => {
        this.members = data;
      });

  }
}
```

### Interview answer

> **ngOnInit is a lifecycle hook called after Angular initializes the component's input properties. It is commonly used for initialization logic such as loading initial data or setting up component state.**

### Common mistake

Don't use the constructor as a replacement for `ngOnInit`.

A constructor is primarily for class construction and dependency injection. Initialization logic that depends on Angular-initialized inputs generally belongs in lifecycle hooks.

---

# 12. Explain ngOnChanges

### What is it?

`ngOnChanges` is called when one or more **data-bound input properties** change.

It is especially useful for parent-to-child communication using `@Input`.

### Why do we use it?

Suppose a parent passes a member to a child:

```text
Parent
  ↓ @Input
Child
```

When the parent changes the input value, the child can react using `ngOnChanges`.

### Real project example

Parent:

```html
<app-member-details
  [member]="selectedMember">
</app-member-details>
```

Child:

```typescript
@Input() member!: Member;
```

When `selectedMember` changes, `ngOnChanges` can respond.

### Code example

```typescript
export class MemberDetailsComponent
  implements OnChanges {

  @Input() member!: Member;

  ngOnChanges(changes: SimpleChanges): void {

    if (changes['member']) {
      console.log('Member changed');
    }

  }
}
```

### Interview answer

> **ngOnChanges is called when Angular detects changes to data-bound input properties of a component or directive. It is commonly used when a child component needs to react when a parent changes an @Input value.**

### Common mistake

❌ Saying `ngOnChanges` runs whenever any component variable changes.

It is specifically related to **input-bound property changes** detected by Angular.

---

# 13. Explain ngOnDestroy

### What is it?

`ngOnDestroy` is called just before Angular destroys a component or directive.

### Why do we use it?

It is mainly used for cleanup.

Examples:

- Unsubscribe from manually managed subscriptions.
- Clear timers.
- Remove event listeners.
- Release resources.
- Stop long-running processes.

### Real project example

Suppose a component subscribes to a manually managed Observable:

```typescript
subscription = this.service.data$
  .subscribe(data => {
    // process data
  });
```

Before the component is destroyed:

```typescript
ngOnDestroy() {
  this.subscription.unsubscribe();
}
```

### Code example

```typescript
export class MemberComponent
  implements OnDestroy {

  private subscription?: Subscription;

  ngOnDestroy(): void {

    this.subscription?.unsubscribe();

  }
}
```

Modern Angular also provides utilities such as `takeUntilDestroyed()` that can reduce manual cleanup code.

### Interview answer

> **ngOnDestroy is called immediately before Angular destroys a component or directive. It is commonly used to clean up manually managed subscriptions, timers, event listeners, and other resources.**

### Common mistake

❌ Saying every Observable must always be manually unsubscribed.

Angular-managed subscriptions such as many `async` pipe usages are handled automatically. The need for manual cleanup depends on how the subscription/resource is created.

---

# 14. Explain ngAfterViewInit

### What is it?

`ngAfterViewInit` is called after Angular has initialized the component's view and child views.

### Why do we use it?

It is useful when we need to interact with something that exists in the component's rendered view.

A common use case is `@ViewChild`.

### Real project example

Suppose we have:

```html
<input #memberInput>
```

and want to access it from TypeScript after the view has been initialized.

### Code example

```typescript
@ViewChild('memberInput')
memberInput!: ElementRef<HTMLInputElement>;

ngAfterViewInit(): void {

  this.memberInput.nativeElement.focus();

}
```

### Interview answer

> **ngAfterViewInit is called after Angular has initialized the component's view and child views. It is commonly used when we need to access view-related elements or child components through ViewChild.**

### Common mistake

Don't access `ViewChild` in `ngOnInit` and assume the view is already initialized.

---

# 15. What is @Input Decorator?

### What is it?

`@Input` allows a **parent component to pass data to a child component**.

Data flow:

```text
Parent
   ↓
Child
```

### Why do we use it?

It allows components to communicate while keeping them reusable.

### Real project example

Parent displays a list and passes the selected member to a child details component.

Parent:

```html
<app-member-details
  [member]="selectedMember">
</app-member-details>
```

Child:

```typescript
@Input() member!: Member;
```

### Code example

Child:

```typescript
export class MemberDetailsComponent {

  @Input() member!: Member;

}
```

Parent:

```html
<app-member-details
  [member]="selectedMember">
</app-member-details>
```

### Interview answer

> **@Input allows a parent component to pass data to a child component. It establishes one-way data flow from parent to child.**

### Common mistake

❌ Saying `@Input` sends data from child to parent.

For child-to-parent communication, use `@Output` with an event.

---

# 16. What is @Output Decorator?

### What is it?

`@Output` allows a child component to expose an event that the parent can listen to.

Data/event flow:

```text
Child
   ↓
Parent
```

### Why do we use it?

It is commonly used when a child needs to notify its parent about an action.

Examples:

- Delete clicked
- Save completed
- Selection changed
- Dialog closed

### Real project example

Child component:

```text
MemberDetailsComponent
       ↓
"Delete member"
       ↓
Parent MemberListComponent
```

### Code example

Child:

```typescript
@Output() memberDeleted =
  new EventEmitter<number>();

deleteMember(id: number) {

  this.memberDeleted.emit(id);

}
```

Parent:

```html
<app-member-details
  (memberDeleted)="onMemberDeleted($event)">
</app-member-details>
```

### Interview answer

> **@Output is used for child-to-parent communication. It exposes an event from the child component that the parent can subscribe to through event binding.**

### Common mistake

Don't confuse:

```text
@Input  → Parent → Child
@Output → Child → Parent
```

---

# 17. What is EventEmitter?

### What is it?

`EventEmitter` is commonly used with `@Output` to emit custom events from a child component.

### Why do we use it?

It allows the child to notify the parent that something happened.

### Real project example

Child:

```typescript
@Output()
saved = new EventEmitter<Member>();
```

After successfully saving:

```typescript
this.saved.emit(this.member);
```

Parent can handle it:

```html
<app-member-form
  (saved)="onMemberSaved($event)">
</app-member-form>
```

### Code example

```typescript
@Output()
deleted = new EventEmitter<number>();

deleteMember(id: number): void {
  this.deleted.emit(id);
}
```

### Interview answer

> **EventEmitter is used with @Output to emit custom events from a child component to its parent. The emitted value can be received by the parent through event binding.**

### Common mistake

❌ Using EventEmitter as a general-purpose application event bus.

For component communication, `@Output` is appropriate. For broader application communication, services/signals/state-management approaches may be more suitable.

---

# 18. What is ViewChild?

### What is it?

`ViewChild` allows a component to obtain a reference to an element, directive, or child component from its own template/view.

### Why do we use it?

It is useful when a component needs direct access to something in its view.

### Real project example

Suppose the parent contains a child component:

```html
<app-member-form></app-member-form>
```

The parent can get a reference to that child:

```typescript
@ViewChild(MemberFormComponent)
memberForm!: MemberFormComponent;
```

It can then call a public method:

```typescript
this.memberForm.resetForm();
```

### Code example

Template:

```html
<input #memberNameInput>
```

Component:

```typescript
@ViewChild('memberNameInput')
memberNameInput!: ElementRef<HTMLInputElement>;
```

After view initialization:

```typescript
ngAfterViewInit(): void {
  this.memberNameInput.nativeElement.focus();
}
```

### Interview answer

> **ViewChild allows a component to access an element, directive, or child component from its own view. It is commonly used for view interaction, accessing child component APIs, or interacting with template elements.**

### Common mistake

Don't use `ViewChild` as the default way to communicate between components.

For normal parent-child data flow:

```text
Parent → Child : @Input
Child → Parent : @Output
```

Use `ViewChild` when direct view/child-instance access is actually required.

---

# 19. What is ContentChild?

### What is it?

`ContentChild` allows a component to access an element, directive, or component that has been **projected into it using content projection**.

The key difference:

```text
ViewChild
→ Component's own template

ContentChild
→ Content projected into the component
```

### Why do we use it?

It is useful with reusable components that accept custom content through `ng-content`.

### Real project example

Reusable card component:

```html
<app-card>
  <p>Member Details</p>
</app-card>
```

Inside `app-card`:

```html
<div class="card">
  <ng-content></ng-content>
</div>
```

The projected `<p>` is **content**, not part of the card component's own template.

### Code example

```typescript
@ContentChild('projectedContent')
content!: ElementRef;
```

Projected content:

```html
<app-card>
  <div #projectedContent>
    Member information
  </div>
</app-card>
```

### Interview answer

> **ContentChild is used to access content that has been projected into a component, typically through ng-content. ViewChild accesses the component's own view, while ContentChild accesses projected content.**

### Common mistake

The easiest way to remember:

```text
ViewChild
→ Inside my template

ContentChild
→ Given to me by the parent through content projection
```

---

# 20. What is ng-content used for?

### What is it?

`ng-content` is used for **content projection**.

It allows a reusable component to accept HTML/content from its parent and render that content inside its own template.

### Why do we use it?

It helps create flexible reusable components.

Instead of hardcoding everything inside a reusable component, the parent can provide custom content.

### Real project example

Reusable card:

Parent:

```html
<app-card>
  <h2>Member Details</h2>
  <p>John is an active member.</p>
</app-card>
```

Card component:

```html
<div class="card">
  <ng-content></ng-content>
</div>
```

Angular projects the parent-provided content into the card.

### Code example

```html
<!-- card.component.html -->

<div class="card">
    <ng-content></ng-content>
</div>
```

Usage:

```html
<app-card>
    <h2>Premium Member</h2>
    <p>Membership is active.</p>
</app-card>
```

### Interview answer

> **ng-content is used for content projection. It allows a parent component to pass HTML content into a reusable child component, where the child determines where that content should be rendered.**

### Common mistake

Don't confuse content projection with `@Input`.

```text
@Input
→ Pass data

ng-content
→ Project content/markup
```

---

# 21. What is a Template Reference Variable?

### What is it?

A **template reference variable** creates a reference to an element, directive, or component instance inside an Angular template.

It is commonly declared using:

```html
#variableName
```

### Why do we use it?

It allows us to refer to a template element directly.

### Real project example

```html
<input #memberName>

<button (click)="showName(memberName.value)">
    Show Name
</button>
```

The input can be accessed directly in the template.

### Code example

```html
<input #nameInput>

<button (click)="nameInput.focus()">
    Focus Input
</button>
```

### Interview answer

> **A template reference variable provides a reference to an element, directive, or component instance within an Angular template. It is declared using the # syntax and can be used to interact with that reference from the template.**

### Common mistake

Don't confuse:

```text
#memberInput
```

with:

```text
@ViewChild('memberInput')
```

The first creates a template reference variable. The second allows the component class to access that template reference.

---

# 22. What is Change Detection in Angular?

### What is it?

**Change detection** is the process Angular uses to determine whether the application's data has changed and whether the UI needs to be updated.

Simplified:

```text
Data changes
     ↓
Angular checks bindings
     ↓
Detects changes
     ↓
Updates DOM
```

### Why do we use it?

Without change detection, changes in component state would not automatically appear in the UI.

### Real project example

Suppose:

```typescript
memberName = 'John';
```

Then:

```typescript
this.memberName = 'David';
```

Angular detects the relevant change and updates:

```html
<h2>{{ memberName }}</h2>
```

from:

```text
John
```

to:

```text
David
```

### Code example

```typescript
updateName() {
  this.memberName = 'David';
}
```

Template:

```html
<h2>{{ memberName }}</h2>

<button (click)="updateName()">
    Change Name
</button>
```

### Interview answer

> **Change detection is Angular's mechanism for checking whether data used by the template has changed and updating the DOM when necessary. Angular's change detection strategy determines how and when these checks are performed.**

### Common mistake

Don't say:

> Angular updates the entire DOM every time.

Angular updates the relevant parts of the rendered view based on its change-detection process.

---

# 23. Difference Between Default and OnPush Change Detection

### What is it?

Angular provides different change-detection strategies. The two commonly discussed strategies are:

```text
Default
OnPush
```

### Default Strategy

With the default strategy, Angular checks the component and its relevant view tree during normal change-detection processing.

It is easier to use but can result in more checking than necessary in large applications.

### OnPush Strategy

`OnPush` makes Angular's checking more targeted.

Example:

```typescript
@Component({
  selector: 'app-member',
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class MemberComponent {
}
```

Angular can check the component when important triggers occur, such as:

- An input reference changes.
- An event occurs in the component/view.
- The component is explicitly marked for checking.
- Reactive mechanisms such as signals notify Angular.

### Why do we use it?

`OnPush` can improve performance in large applications by reducing unnecessary change-detection work.

### Real project example

Suppose we have:

```text
Dashboard
 ├── MemberList
 ├── MemberSummary
 ├── Reports
 └── Notifications
```

Using `OnPush` appropriately can help prevent unrelated updates from causing unnecessary checks throughout large component trees.

### Code example

```typescript
@Component({
  selector: 'app-member-list',
  templateUrl: './member-list.component.html',
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class MemberListComponent {

}
```

Important example:

```typescript
this.member = {
  ...this.member,
  name: 'David'
};
```

This creates a new object reference.

Whereas:

```typescript
this.member.name = 'David';
```

mutates the existing object reference.

Understanding **reference changes and immutability** is important when working with `OnPush`.

### Interview answer

> **The Default change-detection strategy performs broader checking during Angular's normal change-detection process. OnPush allows Angular to perform more targeted checks based on changes such as input reference changes, events, explicit marking, and reactive updates. OnPush can improve performance in large applications when used correctly.**

### Common mistake

❌ Saying:

> OnPush means Angular checks the component only once.

It does not. `OnPush` still allows the component to be checked when its relevant triggers occur.

---

# 24. What is Zone.js?

### What is it?

**Zone.js** is a library historically used by Angular to help detect asynchronous operations and trigger Angular change detection.

Examples of asynchronous operations include:

- `setTimeout`
- Promises
- DOM events
- HTTP requests

Simplified traditional flow:

```text
Async operation
      ↓
Zone.js detects completion
      ↓
Angular runs change detection
      ↓
UI updates
```

### Why do we use it?

Historically, Zone.js made Angular's change detection convenient because Angular didn't need developers to manually tell it every time an asynchronous operation completed.

### Real project example

Suppose an API request completes:

```text
.NET API
   ↓
HTTP response
   ↓
Observable callback
   ↓
Angular detects relevant async activity
   ↓
Change detection
   ↓
UI updated
```

### Code example

```typescript
this.memberService.getMembers()
  .subscribe(members => {

    this.members = members;

  });
```

Traditionally, Zone.js helps Angular know that asynchronous activity occurred so Angular can perform its change-detection work.

### Interview answer

> **Zone.js is a library that historically helped Angular detect asynchronous operations and trigger change detection automatically. Modern Angular also supports zoneless change detection, so Zone.js is no longer a mandatory part of every Angular application's architecture.**

### Common mistake

❌ Saying:

> Zone.js itself updates the DOM.

Zone.js helps Angular become aware of asynchronous activity. **Angular's change-detection mechanism** is responsible for checking bindings and updating the UI.

---

# ⭐ 4-Year Experience Interview Scenario 1

### Interviewer:

> You have a parent MemberListComponent and a child MemberDetailsComponent. The parent needs to send the selected member to the child, and the child needs to notify the parent when the member is deleted. How would you implement it?

### Answer

I would use:

```text
Parent → Child
@Input

Child → Parent
@Output + EventEmitter
```

Child:

```typescript
@Input() member!: Member;

@Output()
deleted = new EventEmitter<number>();

deleteMember() {
  this.deleted.emit(this.member.id);
}
```

Parent:

```html
<app-member-details
  [member]="selectedMember"
  (deleted)="onMemberDeleted($event)">
</app-member-details>
```

This provides clear and predictable component communication.

---

# ⭐ 4-Year Experience Interview Scenario 2

### Interviewer:

> A user is editing a member and accidentally clicks another menu item. You want to ask whether they really want to leave the page. What Angular feature would you use?

### Answer:

I would use a **CanDeactivate route guard**.

Flow:

```text
User edits member
       ↓
Unsaved changes = true
       ↓
User navigates away
       ↓
CanDeactivate
       ↓
Confirm?
   ├── Yes → Navigate
   └── No  → Stay
```

---

# ⭐ 4-Year Experience Interview Scenario 3

### Interviewer:

> Your Angular application has a large Reports module that most users don't open. How would you improve the initial application load?

### Answer:

> I would consider lazy loading the Reports feature so its code is downloaded only when the user navigates to the Reports section. This reduces the initial JavaScript bundle and can improve startup performance.

---

# ⭐ 4-Year Experience Interview Scenario 4

### Interviewer:

> What is the difference between ViewChild and ContentChild?

### Best short answer:

> **ViewChild accesses something from the component's own view, while ContentChild accesses something projected into the component through content projection using ng-content.**

Remember:

```text
ViewChild
→ My template

ContentChild
→ Parent-provided projected content
```

---

# ⭐ 4-Year Experience Interview Scenario 5

### Interviewer:

> Your Angular application is becoming slow because there are many components and frequent UI updates. What would you investigate?

### Answer:

I would first identify where unnecessary change detection or rendering is occurring rather than blindly changing the strategy.

I would investigate:

- Component tree
- Change detection
- `OnPush`
- Large lists
- `@for` tracking
- Expensive template expressions
- Impure pipes
- Unnecessary subscriptions
- Large API responses
- Unnecessary component updates

Then I would apply optimizations based on profiling rather than assuming `OnPush` alone will solve the problem.

---

# ⭐ Important Connections

## Component Communication

```text
                 Parent
                /      \
               ↓        ↑
           @Input      @Output
               ↓        ↑
              Child + EventEmitter
```

---

## Routing

```text
User
 ↓
RouterLink
 ↓
Angular Router
 ↓
Route Guard
 ↓
Resolver (if configured)
 ↓
Route Component
 ↓
RouterOutlet
```

---

## Lifecycle

```text
Component Created
       ↓
ngOnChanges
       ↓
ngOnInit
       ↓
View Initialization
       ↓
ngAfterViewInit
       ↓
Component Runs
       ↓
ngOnDestroy
       ↓
Cleanup
```

> `ngOnChanges` is relevant when there are input-bound changes; it is not simply a mandatory step for every component lifecycle.

---

## Dependency Injection

```text
Component
    ↓
Request Service
    ↓
Angular Injector
    ↓
Search Injector Hierarchy
    ↓
Find Provider
    ↓
Return Dependency
```

---

## Change Detection

```text
Application State Changes
          ↓
Change Detection
          ↓
Check Relevant Bindings
          ↓
Update View
```

---

# ⭐ Quick Revision Table

| Concept            | Main Purpose                                     |
| ------------------ | ------------------------------------------------ |
| Hierarchical DI    | Control dependency scope/instances               |
| Angular Router     | Navigate between application routes              |
| Route Guard        | Allow/block navigation                           |
| CanActivate        | Control entering a route                         |
| CanActivateChild   | Control child-route access                       |
| CanDeactivate      | Control leaving a route                          |
| CanMatch           | Control whether a route matches                  |
| Lazy Loading       | Load feature code on demand                      |
| Resolver           | Load route data before activation                |
| RouterOutlet       | Placeholder for routed component                 |
| RouterLink         | Navigate from template                           |
| ActivatedRoute     | Read current route information                   |
| Lifecycle Hooks    | Execute code at lifecycle stages                 |
| ngOnInit           | Initialization                                   |
| ngOnChanges        | React to input changes                           |
| ngOnDestroy        | Cleanup                                          |
| ngAfterViewInit    | Work with initialized view                       |
| @Input             | Parent → Child                                   |
| @Output            | Child → Parent                                   |
| EventEmitter       | Emit child events                                |
| ViewChild          | Access own view                                  |
| ContentChild       | Access projected content                         |
| ng-content         | Content projection                               |
| Template Reference | Reference template element/directive/component   |
| Change Detection   | Detect state changes and update UI               |
| Default            | Broader normal change detection                  |
| OnPush             | More targeted change detection                   |
| Zone.js            | Historically helps Angular detect async activity |

---

# ⭐ One-Line Interview Revision

```text
Hierarchical DI → Dependency scope hierarchy
Router          → Application navigation
Guard           → Control navigation
CanActivate     → Enter route
CanDeactivate   → Leave route
Lazy Loading    → Load feature when needed
Resolver        → Load route data before activation
RouterOutlet    → Render routed component
RouterLink      → Navigate from template
ActivatedRoute  → Read route information

Lifecycle Hooks → Run code at lifecycle stages
ngOnInit        → Initialize
ngOnChanges     → React to @Input changes
ngAfterViewInit → View is initialized
ngOnDestroy     → Cleanup

@Input          → Parent → Child
@Output         → Child → Parent
EventEmitter    → Emit child event
ViewChild       → Access own view
ContentChild    → Access projected content
ng-content      → Content projection
#variable       → Template reference

Change Detection → Detect changes and update UI
Default          → Normal/broader checking
OnPush           → Targeted checking
Zone.js          → Historically detects async activity for Angular
```

---

# ⚠️ Modern Angular Interview Notes

For a **4-year Angular interview**, know the traditional concepts because many enterprise projects still use them, but also understand the modern equivalents.

### Traditional

```html
*ngIf
*ngFor
```

### Modern

```html
@if (...)
@for (...)
```

---

### Traditional module-based application

```text
AppModule
   ↓
Feature Modules
   ↓
Components
```

### Modern Angular

```text
Application
   ↓
Standalone Components
   ↓
Standalone Routes
```

---

### Traditional Zone-based change detection

```text
Async operation
      ↓
Zone.js
      ↓
Change Detection
```

### Modern Angular

Angular can also run with **zoneless change detection**, so don't answer that Zone.js is mandatory for every Angular application.

---

# 🎯 Interview Rule for This Section

When answering these topics in an interview, don't stop at the definition.

Use this pattern:

```text
1. What is it?
       ↓
2. Why do we use it?
       ↓
3. Real project example
       ↓
4. Code/syntax
       ↓
5. Important limitation/common mistake
```

For a **4-year developer**, interviewers are much more likely to continue with:

> "Okay, where have you used this in your project?"

So your goal is not just to memorize the definition — be able to connect every concept to your **Angular + .NET Membership Management project**.

