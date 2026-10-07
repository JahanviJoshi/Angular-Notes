# Angular-Notes

**1. What is Angular? 
What is it?**
Angular is a TypeScript-based frontend framework developed by Google for building single-page applications (SPAs).
Angular provides a complete structure for building applications using concepts such as:
    Components
    Templates
    Data binding
    Dependency Injection
    Services
    Routing
    Forms
    HTTP communication
    Directives
    Pipes
    Modules

Unlike using plain JavaScript or a lightweight library, Angular provides an opinionated application structure, which makes it suitable for large and enterprise applications.

**Why do we use it?**
We use Angular to:
Build dynamic web applications.
Create reusable UI components.
Communicate with backend APIs.
Manage application state and data.
Implement routing/navigation.
Perform form validation.
Maintain large applications with a structured architecture.
Improve code reusability and maintainability.

**Real project example**
Suppose we have a Membership Management System.
The Angular application may contain:
Login
   ↓
Dashboard
   ↓
Member Management
   ├── Member List
   ├── Add Member
   ├── Edit Member
   └── Member Details

Angular components handle the UI, services communicate with the .NET APIs, and routing handles navigation.

**For example:**
Angular
   ↓
MemberComponent
   ↓
MemberService
   ↓
.NET Web API
   ↓
MySQL

Code example

A simple Angular component:

@Component({
  selector: 'app-member',
  template: `
    <h2>Member Management</h2>
  `
})
export class MemberComponent {

}

**Interview answer**
Angular is a TypeScript-based frontend framework developed by Google for building scalable single-page applications. It provides features like component-based architecture, data binding, dependency injection, routing, forms, directives, and HTTP communication, which makes it suitable for developing large enterprise applications.

**Common mistake**
❌ Saying:
Angular is a JavaScript library.

Angular is a framework, not just a library.

❌ Saying Angular is only used for UI.

Angular also provides application-level features such as routing, dependency injection, forms, HTTP communication, and application architecture.

**2. Difference Between Angular and AngularJS**
**What is it?**
AngularJS refers to the older Angular framework, mainly based on JavaScript.
Angular refers to the modern framework that was completely redesigned and is primarily based on TypeScript.
AngularJS and Angular are not simply different versions of the same architecture. Angular was a major rewrite.

**Why do we use it?**
Understanding the difference is important because interviewers often ask this when they see Angular experience on a resume.

**Real project example**
An older application might use:

AngularJS
Controllers
$scope
Two-way binding

A modern Angular application typically uses:

Angular
Components
Services
Dependency Injection
TypeScript
RxJS
Routing

**Code example**

AngularJS

app.controller('MemberController', function($scope) {

    $scope.memberName = "John";

});

Angular

export class MemberComponent {

  memberName = "John";

}

Template:

<h2>{{ memberName }}</h2>

**Interview answer**

AngularJS is the older JavaScript-based framework, whereas Angular is the modern TypeScript-based framework that was redesigned from the ground up. Angular uses component-based architecture, improved dependency injection, TypeScript, better tooling, and improved support for large-scale applications.

**Common mistake**

❌ Saying:

Angular is just AngularJS with a newer version.

Angular is a major architectural rewrite.

**3. What is a Component in Angular?**
**What is it?**
A Component is one of the fundamental building blocks of an Angular application.
A component controls a specific part of the UI.
A component generally contains:

Component
├── TypeScript class
├── HTML template
└── CSS/SCSS styles

The TypeScript class contains the component's logic and data, while the template defines what is displayed on the screen.

**Why do we use it?**
  Components help us:
  Break a large UI into smaller pieces.
  Reuse UI functionality.
  Separate business/UI responsibilities.
  Make applications easier to maintain and test.

**Real project example**
In a Membership Management application:

MemberListComponent
MemberAddComponent
MemberEditComponent
MemberDetailsComponent
LoginComponent
DashboardComponent

Each component has a specific responsibility.

For example:

MemberListComponent
        ↓
Displays members
        ↓
Calls MemberService
        ↓
Gets data from .NET API

Code example

@Component({
  selector: 'app-member',
  templateUrl: './member.component.html',
  styleUrls: ['./member.component.css']
})
export class MemberComponent {

  memberName = 'John';

}

HTML:

<h2>Member Name: {{ memberName }}</h2>

**Interview answer**

A component is a fundamental building block of Angular applications. It controls a specific part of the UI and consists of a TypeScript class, template, and styles. Components help us divide the application into reusable and maintainable UI sections.
Common mistake

❌ Thinking that a component contains only HTML.

A component combines:

UI template

Component logic

Styling

Metadata/configuration

**4. What is a Module (NgModule)?**
**What is it?**
An NgModule is a mechanism used to organize Angular applications by grouping related Angular components, directives, pipes, and services.
It is defined using the @NgModule decorator.
Important for modern Angular: Standalone components are now also supported and are increasingly common. Therefore, don't assume every modern Angular application must use NgModule. However, many enterprise/legacy Angular applications still use modules.

**Why do we use it?**
NgModules help organize large applications into logical sections.

**For example:**
Application
│
├── CoreModule
├── SharedModule
├── MemberModule
└── AdminModule

This makes large applications easier to maintain.

**Real project example**
A membership application might have:
MemberModule
│
├── MemberListComponent
├── MemberAddComponent
├── MemberEditComponent
└── MemberDetailsComponent

All member-related functionality can be grouped together.

**Code example**

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

**Interview answer**
NgModule is an Angular mechanism used to organize related components, directives, pipes, and services into cohesive functional areas. It helps structure larger applications. However, modern Angular also supports standalone components, so NgModules are no longer mandatory for every application.

**Common mistake**

❌ Saying:

Every Angular application must use NgModules.
Modern Angular supports standalone components, so this statement is outdated.

**5. What is a Root Module (AppModule)?**
**What is it?**

AppModule traditionally acts as the root NgModule of an Angular application.
It is the starting point from which Angular bootstraps the application.
In older/module-based Angular applications, AppModule commonly contains:
  Root component
  Required imports
  Application-level providers
  Bootstrap configuration

**Why do we use it?**
It provides the starting structure for a module-based Angular application.

**Real project example**
A traditional Angular application might look like:

AppModule
   ↓
AppComponent
   ↓
Router
   ↓
Feature Components

For example:

AppModule
 ├── AppComponent
 ├── MemberModule
 ├── AdminModule
 └── SharedModule

Code example

Traditional Angular application:

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

**Interview answer**
AppModule is traditionally the root NgModule of a module-based Angular application. It acts as the entry point for bootstrapping the root component and configuring application-level dependencies. In modern Angular, standalone bootstrapping can be used instead, so AppModule is not mandatory.

**Common mistake**

❌ Saying:
AppModule is mandatory in every Angular application.

Modern Angular applications can use standalone bootstrapping.

**6. What is a Feature Module?**
**What is it?**
A Feature Module is an NgModule created to group functionality related to a specific business feature.
For example:
  MemberModule
  OrderModule
  PaymentModule
  AdminModule
Each module contains functionality related to that feature.

**Why do we use it?**
Feature modules help:
Organize large applications.
Separate business functionality.
Improve maintainability.
Support lazy loading.
Reduce complexity in the root application structure.

**Real project example**
In a Membership Management application:

MemberModule
│
├── MemberListComponent
├── MemberDetailsComponent
├── MemberAddComponent
├── MemberEditComponent
├── MemberService
└── MemberRoutingModule

The member-related functionality stays together.

If the Member feature is lazy-loaded, Angular can load it only when the user navigates to the member section.

**Code example**

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

**Interview answer**
A feature module groups components, directives, pipes, and related functionality belonging to a specific business feature. For example, in a membership application, MemberModule can contain member-related components and routing. Feature modules improve organization and can also support lazy loading.

**Common mistake**
❌ Creating one huge module containing every component in the application.
Large applications should be organized around meaningful features.

**7. What is a Component Decorator?**
**What is it?**
The @Component decorator provides metadata that tells Angular that a TypeScript class should be treated as a component.
It defines information such as:
  Component selector
  Template
  Styles
  Other component metadata

**Why do we use it?**
Without the appropriate component metadata, Angular would not know:
Which class represents the component.
Which HTML template belongs to it.
Which selector should be used.
Which styles belong to the component.

**Real project example**
For a member component:

@Component({
  selector: 'app-member',
  templateUrl: './member.component.html',
  styleUrls: ['./member.component.css']
})
export class MemberComponent {

}

The selector:
<app-member></app-member>
can then be used to render the component.

**Code example**

@Component({
  selector: 'app-dashboard',
  template: `
    <h1>Dashboard</h1>
  `
})
export class DashboardComponent {

}

**Interview answer**
The @Component decorator provides metadata that tells Angular how to create and render a component. It defines information such as the selector, template, and styles associated with the component class.

**Common mistake**
❌ Saying:

@Component is the component itself.

The TypeScript class represents the component logic, while @Component provides Angular metadata describing how that class should be treated as a component.

**8. What is a Template in Angular?**
**What is it?**
A template is the HTML structure that defines the UI of an Angular component.
Angular templates are more powerful than normal HTML because they support Angular features such as:
  Interpolation
  Property binding
  Event binding
  Structural/control flow
  Directives
  Pipes
  Template expressions

**Why do we use it?**
Templates allow us to connect the component's data and logic with the UI.

**Real project example**
Suppose the component contains:
memberName = 'John';
The template can display it:
<h2>{{ memberName }}</h2>
If the value changes, Angular updates the UI accordingly.

**Code example**

export class MemberComponent {
  memberName = 'John';
  isActive = true;
}

Template:

<h2>{{ memberName }}</h2>

<button [disabled]="!isActive">
  Edit Member
</button>

**Interview answer**
An Angular template defines the UI of a component using HTML enhanced with Angular template syntax. It allows us to display component data and interact with the component through binding, events, directives, control flow, and pipes.

**Common mistake**
❌ Thinking templates are only static HTML.
Angular templates can dynamically interact with component data and user events.

**9. What is Data Binding?**
**What is it?**
Data binding is the mechanism that connects the component's data/logic with the template/UI.
It allows information to move between:
Component Class
       ↕
    Template

**For example:**
memberName = "John";
can be displayed in HTML using:

{{ memberName }}

**Why do we use it?**
Data binding helps us:
Display dynamic data.
Pass data to UI elements.
Respond to user events.
Synchronize form values with component data.
Without data binding, we would need to manually manipulate the DOM for many UI updates.

**Real project example**
Suppose the API returns:
{
  "id": 101,
  "name": "John",
  "isActive": true
}
The Angular component stores this data:

member = {
  id: 101,
  name: 'John',
  isActive: true
};

The template can display:

<h2>{{ member.name }}</h2>

And bind the active status:

<input type="checkbox" [checked]="member.isActive">

**Code example**

<!-- Component → Template -->
<h2>{{ member.name }}</h2>

<!-- Template → Component -->
<button (click)="deleteMember()">
  Delete
</button>

<!-- Two-way -->
<input [(ngModel)]="member.name">

**Interview answer**
Data binding is the mechanism Angular provides to establish communication between a component class and its template. It allows us to display component data, bind properties, handle user events, and synchronize UI values with component state.

**Common mistake**
❌ Saying data binding means only interpolation.
Interpolation is only one type of Angular data binding.

**10. Types of Data Binding**
**What is it?**

Angular primarily provides four commonly discussed types of data binding:

1. Interpolation
2. Property Binding
3. Event Binding
4. Two-Way Binding

**10.1 Interpolation**
**What is it?**
Interpolation displays component data in the HTML using:
{{ expression }}

**Code example**
memberName = 'John';
<h2>{{ memberName }}</h2>

**Real project example**

Displaying a logged-in user's name:

Welcome, {{ userName }}

**Interview answer**
Interpolation is used to display component data in the template using double curly braces.

**10.2 Property Binding**
**What is it?**

Property binding binds a component value to a DOM element or Angular component property.

**Syntax:**
[property]="expression"

**Code example**
isDisabled = true;
<button [disabled]="isDisabled">
  Save
</button>

**Real project example**
Disable the Save button while an API request is running:
isSaving = true;

<button [disabled]="isSaving">
  Save Member
</button>

**Interview answer**

Property binding allows us to dynamically set a DOM or component property using a value from the component.

**10.3 Event Binding**
**What is it?**

Event binding allows the template to send user actions/events to the component.

**Syntax:**
(event)="method()"

**Code example**
<button (click)="deleteMember()">
  Delete
</button>

Component:

deleteMember() {
  console.log('Member deleted');
}

**Real project example**
When the user clicks Delete:

User clicks Delete
       ↓
(click)
       ↓
deleteMember()
       ↓
API call
       ↓
Delete member

Interview answer

Event binding allows Angular to respond to events generated by the user or DOM, such as click, input, change, and submit events.

10.4 Two-Way Data Binding

What is it?

Two-way binding allows data to flow in both directions:

Component
   ↕
Template

Angular commonly uses:

[(ngModel)]

This syntax is called banana-in-a-box syntax.

**Code example**

memberName = 'John';
<input [(ngModel)]="memberName">
<p>{{ memberName }}</p>
If the user changes the input:
Input
  ↓
memberName updated
  ↓
UI updated

**Real project example**

For editing a member:
<input [(ngModel)]="member.name">
When the user changes the name, the component's member.name is updated.

**Interview answer**
Two-way data binding keeps the component value and UI value synchronized. In template-driven forms, Angular commonly provides this through [(ngModel)].

**Common mistake**

❌ Saying:

Two-way binding is always the best approach.
For large enterprise applications, especially complex forms, Reactive Forms are often preferred because they provide stronger programmatic control, validation, and testability.
Data Binding — Quick Interview Table
Binding Type

Direction

**Syntax**

**Example**

**Interpolation**

Component → Template

{{ }}

{{member.name}}

**Property Binding**

Component → Template

[ ]

[disabled]="isDisabled"

**Event Binding**

Template → Component

( )

(click)="save()"

**Two-Way Binding**

Component ↔ Template

[( )]

[(ngModel)]="name"

**⭐ 4-Year Experience Interview Scenario**

Scenario
**Interviewer:**
You have a Save button in your Angular application. While the API request is running, the button should be disabled. How would you implement it?

**Answer**
I would maintain a loading state in the component:
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

Template:

<button
  [disabled]="isSaving"
  (click)="saveMember()">
  Save
</button>

Here:

[disabled] → Property Binding
(click) → Event Binding
isSaving → Component state

**Why is this a good 4-year answer?**
Because instead of only defining property binding, you're showing how Angular binding is used in a real application scenario.

**⭐ Important 4-Year Experience Points**

Remember these connections:

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

And for application architecture:

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

Modern Angular point

For interviews, be aware that Angular has evolved beyond the traditional AppModule/NgModule architecture.

Modern Angular supports:

Standalone components

Standalone bootstrapping

Modern control-flow syntax

Signals

Functional APIs

So if your current project uses modules, understand them well, but don't answer that NgModules are mandatory in every modern Angular application.


**Angular Data Binding, Directives, Pipes & Dependency Injection**

**Target: 4 Years Experience
Focus: Interview + Real Project Understanding
Stack: Angular + .NET Web API**

**1. What is Interpolation?**
**What is it?**

Interpolation is used to display component data inside an Angular template.
It uses double curly braces:
{{ expression }}
The data flows from:
Component
    ↓
Template

**Why do we use it?**
We use interpolation when we want to display dynamic values in the UI.

**Common examples:**
Display username
Display member name
Display API response
Display calculated values
Display status messages

**Real project example**
Suppose our component receives member information from an API:

memberName = 'John';
membershipType = 'Premium';

Template:

<h2>{{ memberName }}</h2>
<p>Membership: {{ membershipType }}</p>

The UI displays:

John
Membership: Premium

**Code example**

export class MemberComponent {

  memberName = 'John';
  age = 30;

}

<h2>{{ memberName }}</h2>
<p>Age: {{ age }}</p>

**Interview answer**
Interpolation is an Angular template syntax used to display component data in the HTML using double curly braces. It is mainly used for one-way data flow from the component to the template.

**Common mistake**

❌ Saying interpolation can be used for everything.

**For example:**

<button disabled="{{ isDisabled }}">
Although Angular can evaluate interpolation in many attributes, property binding is the clearer and preferred approach for DOM properties:
<button [disabled]="isDisabled">

**2. What is Property Binding?**
**What is it?**

Property binding allows us to bind a component value to a DOM element property or Angular component property.
Syntax:
[property]="expression"

**Data flows:**

Component
    ↓
Template

**Why do we use it?**
We use property binding when a value needs to dynamically control an element.

**Examples:**

Disable a button
Set an image source
Set input value
Control visibility/state
Pass data to a child component
Real project example

Suppose a Save button should be disabled while an API request is running.
isSaving = true;

Template:

<button [disabled]="isSaving">
    Save Member
</button>

When:

isSaving = true

the button becomes disabled.

**Code example**

isDisabled = true;
imageUrl = 'assets/member.png';

<button [disabled]="isDisabled">
    Save
</button>

<img [src]="imageUrl">

**Interview answer**
Property binding is used to dynamically set a DOM element or Angular component property using a value from the component. It provides one-way data flow from the component to the template.

**Common mistake**

Don't confuse:
[disabled]="isDisabled"

with:
disabled="isDisabled"

The second one is treated as a literal attribute value rather than Angular property binding.

**3. What is Event Binding?**
**What is it?**
Event binding allows Angular to listen to events from the template and execute component logic.

Syntax:

(event)="method()"

Data/event flow:

Template
    ↓
Component

**Why do we use it?**
We use event binding to respond to user actions such as:
    Click
    Input
    Change
    Submit
    Key press
    Mouse events

**Real project example**
When the user clicks the Delete button:

<button (click)="deleteMember()">
    Delete
</button>

Angular calls:

deleteMember() {
    // Delete member logic
}

**Code example**

deleteMember() {
    console.log('Member deleted');
}

<button (click)="deleteMember()">
    Delete
</button>

You can also access the event:

<input (input)="onInput($event)">

onInput(event: Event) {
    const value = (event.target as HTMLInputElement).value;
    console.log(value);
}

**Interview answer**

Event binding allows the Angular template to communicate user or DOM events to the component. It is represented using parentheses and is commonly used for events such as click, input, change, and submit.

**Common mistake**

❌ Thinking (click) is a function.

It is event binding that tells Angular which component method should execute when the click event occurs.

**4. What is Two-Way Data Binding?
What is it?**
Two-way data binding means that data can flow in both directions:

Component
    ↕
Template

A common Angular syntax is:

[(ngModel)]

This is often called banana-in-a-box syntax.

**Why do we use it?**
It is useful when the UI and component property need to stay synchronized.

**Common example:**
    Forms
    Search fields
    Editable values
    User input

**Real project example**
Suppose we have an edit-member screen.

memberName = 'John';

Template:

<input [(ngModel)]="memberName">

<p>{{ memberName }}</p>

If the user changes:

John → Jahanvi

the component's memberName is also updated.

**Code example**

memberName = '';

<input [(ngModel)]="memberName">

<p>Hello {{ memberName }}</p>

**Interview answer**

Two-way data binding synchronizes a value between the component and the template. When the component value changes, the UI updates, and when the user changes the UI value, the component value is updated. In template-driven forms, [(ngModel)] is commonly used for this.

**Common mistake**

Don't say:
Angular always uses two-way binding.
Angular supports multiple binding patterns. One-way binding is often preferred where possible because it makes data flow easier to understand.

**5. What is ngModel?**
**What is it?**
ngModel is an Angular directive commonly used for two-way data binding in template-driven forms.

Syntax:
[(ngModel)]="property"

**Why do we use it?**
ngModel helps synchronize form controls with component properties.
It can also participate in Angular's template-driven form features such as validation and form state.

**Real project example**

Member registration form:

<input
  type="text"
  [(ngModel)]="member.name">

Component:

member = {
    name: ''
};

When the user types a name, member.name is updated.

**Code example**
memberName = '';

<label>Member Name</label>

<input
  type="text"
  [(ngModel)]="memberName">

<p>Entered: {{ memberName }}</p>

Interview answer

ngModel is an Angular directive used primarily in template-driven forms to bind form controls to component properties. When used with [(ngModel)], it provides two-way data binding.

**Common mistake**

❌ Saying:
ngModel is only for two-way binding.
It can also be used as:
[ngModel]="memberName"

or:

(ngModelChange)="onNameChange($event)"
But [(ngModel)] combines the two.

**6. What is a Directive?**
**What is it?**
A directive is a class that allows us to add behavior to DOM elements or change how Angular handles them.

**Angular directives can be used to:**
Change the appearance of an element.
Change element behavior.
Dynamically create/remove elements.
Respond to changes.
Reuse DOM-related behavior.

**Why do we use it?**
Directives allow us to add reusable behavior to HTML elements without creating a complete component.

**Real project example**
Suppose inactive members should appear differently.

**We can use:**

<div [ngClass]="{'inactive': !member.isActive}">
    {{ member.name }}
</div>
Here ngClass changes the CSS classes based on the member's state.

**Code example**

<p *ngIf="isLoggedIn">
    Welcome back!
</p>
Here ngIf controls whether the element exists in the rendered view.

**Interview answer**

A directive is a class that adds behavior or changes the structure or appearance of DOM elements. Angular provides built-in directives such as ngClass and ngStyle, and developers can also create custom directives.

**Common mistake**
❌ Saying:
Every directive is a component.
A component is a specialized Angular construct with a template. A directive generally attaches behavior to an existing element.

**7. Difference Between Structural and Attribute Directives**
**What is it?**

Angular directives are commonly discussed as:

Structural Directives
Attribute Directives

**Why do we use it?**
The key difference is what they change.

**Structural Directive**
A structural directive changes the structure of the DOM/view.
Examples in traditional Angular syntax:

*ngIf
*ngFor

They can add/remove/repeat views.

**Attribute Directive**
An attribute directive changes the appearance or behavior of an existing element.

**Examples:**

ngClass
ngStyle

**Real project example**

**Structural**
Show member only when active:

<div *ngIf="member.isActive">
    {{ member.name }}
</div>

The view is conditionally created.

**Attribute**

Change the class:

<div [ngClass]="{
    'active': member.isActive,
    'inactive': !member.isActive
}">
    {{ member.name }}
</div>

The element remains, but its styling changes.

**Code example**
Type
Purpose
Examples
Structural
Changes DOM/view structure
*ngIf, *ngFor
Attribute
Changes appearance/behavior
ngClass, ngStyle

**Interview answer**

**Structural directives change the structure of the rendered view by adding, removing, or repeating elements. Attribute directives modify the behavior or appearance of an existing element. Traditional examples are ngIf and ngFor for structural behavior, and ngClass and ngStyle for attribute behavior.

**Common mistake**
❌ Saying structural directives only hide elements.
For example, *ngFor doesn't simply hide elements; it creates multiple views based on a collection.

**8. What is *ngIf?**
**What is it?**

*ngIf is the traditional Angular structural directive used to conditionally render a template.

**Example:**
<div *ngIf="isLoggedIn">
    Welcome!
</div>

If:

isLoggedIn = true;

the content is rendered.

If:

isLoggedIn = false;

the view is not rendered.

**Why do we use it?**
**Common uses:**
    Show/hide sections.
    Display loading messages.
    Show error messages.
    Display content based on permissions.
    Show buttons based on user roles.

**Real project example**

Display an Edit button only when the member is active:
<button *ngIf="member.isActive">
    Edit
</button>

**Code example**

isLoading = true;
<div *ngIf="isLoading">
    Loading members...
</div>

**Interview answer**
*Traditionally, ngIf is a structural directive used to conditionally add or remove a view from the rendered DOM based on an expression. In modern Angular, the equivalent built-in control-flow syntax is @if.

**Common mistake**

Don't say:
*ngIf just changes CSS display to none.
It is fundamentally about conditional view rendering, not simply setting CSS.

**9. What is *ngFor?**
**What is it?**
*ngFor is the traditional Angular structural directive used to iterate over a collection and create a view for each item.

**Why do we use it?**
We use it to display lists such as:
    Members
    Products
    Orders
    Employees
    Transactions

**Real project example**
Suppose the API returns:

members = [
    { id: 1, name: 'John' },
    { id: 2, name: 'David' },
    { id: 3, name: 'Sarah' }
];

Template:

<div *ngFor="let member of members">
    {{ member.name }}
</div>

Output:

John
David
Sarah

Code example

<ul>
    <li *ngFor="let member of members">
        {{ member.name }}
    </li>
</ul>

In older Angular versions, you may also see:

*ngFor="let member of members; index as i"

**Interview answer**
*Traditionally, ngFor is a structural directive used to iterate over a collection and create a template instance for each item. In modern Angular, @for is the newer built-in control-flow syntax.

**Common mistake**
❌ Using *ngFor without considering performance for large lists.
For large collections, Angular's modern @for syntax and appropriate tracking can help Angular efficiently identify which items changed.

**10. What is ngClass?**
**What is it?**
ngClass is an Angular attribute directive used to dynamically add or remove CSS classes.

**Why do we use it?**
It is useful when styling depends on application state.

**Examples:**
Active/inactive
Success/error
Selected/unselected
Valid/invalid

**Real project example**
member.isActive = true;

<div
  [ngClass]="{
    'active-member': member.isActive,
    'inactive-member': !member.isActive
  }">
    {{ member.name }}
</div>

Code example

<div [ngClass]="currentClass">
    Member
</div>

Component:

currentClass = 'active-member';

**Interview answer**
ngClass is an Angular attribute directive used to dynamically add or remove CSS classes based on component data or conditions.

**Common mistake**
For a single simple class, [class.someClass] may be simpler:
<div [class.active]="member.isActive">
Use ngClass when you need more dynamic class handling.

**11. What is ngStyle?**
**What is it?**
ngStyle is an Angular attribute directive used to dynamically set inline CSS styles.

**Why do we use it?**
We use it when styling depends dynamically on component data.

**Real project example**
Display membership status with different styling:

<div
  [ngStyle]="{
    'font-size.px': fontSize,
    'font-weight': 'bold'
  }">
    Premium Member
</div>

**Code example**

fontSize = 18;

<p [ngStyle]="{
    'font-size.px': fontSize
}">
    Member Details
</p>

**Interview answer**
ngStyle is an Angular attribute directive used to dynamically apply inline styles based on component properties or expressions.

**Common mistake**
Don't use ngStyle for every styling requirement.
For static styling, normal CSS classes are generally cleaner:
<div class="member-card">
Use dynamic class/style binding when the value actually depends on application state.

**12. What is a Pipe?**
**What is it?**
A pipe transforms data in an Angular template for display without changing the original component data.

**Syntax:**

{{ value | pipeName }}

Angular provides built-in pipes such as:

date
currency
uppercase
lowercase
number
percent
json

**Why do we use it?**
Pipes are useful for presentation formatting.

**For example:**
2026-10-06
can be displayed as:
06/10/2026

**Real project example**
Display membership registration date:

<p>
    Joined: {{ member.joinedDate | date:'dd/MM/yyyy' }}
</p>

Display membership fee:

<p>
    Fee: {{ member.fee | currency:'INR' }}
</p>

Code example

<p>{{ member.name | uppercase }}</p>

<p>{{ member.joinedDate | date:'dd/MM/yyyy' }}</p>

<p>{{ member.fee | currency:'INR' }}</p>

**Interview answer**
A pipe transforms data for presentation in an Angular template. Angular provides built-in pipes such as date, currency, uppercase, and number, and we can also create custom pipes for application-specific transformations.

**Common mistake**
❌ Using pipes for complex business logic.

Pipes should generally focus on presentation transformation, not major business operations.

**13. What is a Custom Pipe?**
**What is it?**

A custom pipe is a pipe created by the developer for application-specific data transformation.
We create one using the @Pipe decorator.

**Why do we use it?**

When Angular's built-in pipes don't meet our requirement, we can create our own.

**Real project example**

Suppose our application stores membership status as:

A
I

But the UI should display:

Active
Inactive

A custom pipe can handle this transformation.

Code example

import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'membershipStatus'
})
export class MembershipStatusPipe implements PipeTransform {

  transform(status: string): string {
    return status === 'A' ? 'Active' : 'Inactive';
  }

}

Template:

<p>
    Status: {{ member.status | membershipStatus }}
</p>

**Interview answer**
A custom pipe is a developer-created pipe used to perform application-specific presentation transformations that are not provided by Angular's built-in pipes.

**Common mistake**
Don't put complex business logic or API calls inside a pipe.
A pipe should generally remain focused on transforming data for display.

**14. What is a Pure vs Impure Pipe?**
**What is it?**
Angular pipes are pure by default.
The difference is related to when Angular executes the pipe.

**Pure Pipe**
A pure pipe runs when Angular detects a change to the pipe's input value or its input arguments.

**Example:**

@Pipe({
  name: 'membershipStatus',
  pure: true
})

Pure pipes are generally more efficient because Angular doesn't need to execute them on every change-detection cycle.

**Impure Pipe**

An impure pipe is declared with:

@Pipe({
  name: 'myPipe',
  pure: false
})

Angular may execute it during every change-detection cycle.

**Why do we use them?**
Pure pipes are preferred for most transformations because they provide better performance and predictable behavior.
Impure pipes are useful when the output needs to respond to changes that Angular's normal pure-pipe input checking would not detect, such as certain in-place mutations.

**Real project example**
Suppose we have:

members = [
    { name: 'John' },
    { name: 'David' }
];

A pure pipe works well when a new array reference is supplied:
this.members = [...this.members, newMember];
However, if we mutate the existing array:
this.members.push(newMember);
the array reference remains the same.
This is one reason understanding immutability/reference changes matters when working with pure pipes.

**Code example**

**Pure:**

@Pipe({
  name: 'uppercaseName',
  pure: true
})
export class UppercaseNamePipe implements PipeTransform {

  transform(name: string): string {
    return name.toUpperCase();
  }

}

**Impure:**

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

**Interview answer**
Angular pipes are pure by default. A pure pipe is evaluated when its input value or arguments change, while an impure pipe can be evaluated during every change-detection cycle. Pure pipes are generally preferred for performance, and impure pipes should be used carefully.

**Common mistake**
❌ Saying:
Pure pipes run only once.
They don't necessarily run only once. They run when Angular determines their input or arguments have changed.

**15. What is Dependency Injection in Angular?**
**What is it?**

Dependency Injection (DI) is a design pattern where a class receives the objects/services it depends on instead of creating them itself.
Without DI:

export class MemberComponent {

  service = new MemberService();

}

With DI:

export class MemberComponent {

  constructor(private memberService: MemberService) {}

}

Angular's DI system provides the required dependency.

**Why do we use it?**
DI provides:
Loose coupling
Reusability
Testability
Centralized dependency management
Easier maintenance

**Real project example**
A component should not directly create an API service.

**Instead:**
MemberComponent
      ↓
MemberService
      ↓
HttpClient
      ↓
.NET API

Angular injects MemberService into MemberComponent.

**Code example**

Service:

@Injectable({
  providedIn: 'root'
})
export class MemberService {

  getMembers() {
    // API call
  }

}

Component:

export class MemberComponent {

  constructor(
    private memberService: MemberService
  ) {}

}

Angular creates/provides the service according to its DI configuration.

**Interview answer**
Dependency Injection is a design pattern used by Angular to provide a class with its required dependencies rather than having the class create them directly. Angular has a built-in hierarchical DI system, which improves loose coupling, reusability, maintainability, and testability.

**Common mistake**
❌ Saying:
DI means creating an object inside the constructor.
The important concept is that the dependency is provided by Angular's DI system, rather than manually creating it with new.

**16. What is a Service in Angular?**
**What is it?**

A service is a TypeScript class used to encapsulate reusable application logic or functionality.

**Services commonly handle:**
API calls
Business-related client logic
Shared data
Authentication
Logging
State-related functionality

**Why do we use it?**
Services help keep components focused on UI responsibilities.
Instead of putting API calls directly inside a component:

Component
    ↓
Service
    ↓
HTTP API

**Real project example**

For a membership application:
MemberComponent
       ↓
MemberService
       ↓
HttpClient
       ↓
.NET Web API
       ↓
MySQL

MemberService can contain methods such as:

getMembers()
getMemberById()
addMember()
updateMember()
deleteMember()

**Code example**

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

Component:

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

**Interview answer**

An Angular service is a reusable class that encapsulates functionality that should be shared or separated from component UI logic. A common use case is placing HTTP/API communication in services and injecting those services into components using Angular's dependency injection system.

**Common mistake**

❌ Saying:

Every service must call an API.

Services don't have to call APIs. They can contain authentication logic, shared state, logging, calculations, or other reusable functionality.

**17. What is the @Injectable Decorator?
What is it?**

@Injectable is a decorator that tells Angular that a class participates in Angular's dependency injection system.

It is commonly used on services.

Example:

@Injectable({
  providedIn: 'root'
})
export class MemberService {

}

**Why do we use it?**

It allows Angular to understand how the class should participate in dependency injection and what dependencies it may need.

For example:

@Injectable({
  providedIn: 'root'
})
export class MemberService {

  constructor(private http: HttpClient) {}

}

Angular can resolve HttpClient and inject it into the service.

**Real project example**
A member service depends on HttpClient:

MemberComponent
       ↓
MemberService
       ↓
HttpClient

Angular's DI system resolves these dependencies.

Code example

@Injectable({
  providedIn: 'root'
})
export class MemberService {

  constructor(
    private http: HttpClient
  ) {}

}

**Interview answer**
@Injectable is an Angular decorator that marks a class as available for dependency injection and provides metadata Angular can use to resolve its dependencies. It is commonly used with services.

**Common mistake**

❌ Saying:

@Injectable means the class is automatically a singleton.
That is not the complete explanation.
The lifetime/scope depends on where the provider is registered.

**18. What is providedIn: 'root'?**
**What is it?**

When we write:

@Injectable({
  providedIn: 'root'
})

we are telling Angular to provide the service through the root injector.
For the usual application setup, this means the service is available throughout the application and typically behaves as a singleton instance within that application's injector.

**Why do we use it?**
Benefits include:
Application-wide availability.
No need to manually register the service in a module's providers in the common case.
Tree-shakable provider configuration.
Clear service scope.

**Real project example**

For an application-wide authentication service:

@Injectable({
  providedIn: 'root'
})
export class AuthService {

  isLoggedIn = false;

}

Different components can inject the service:

LoginComponent
       ↓
   AuthService
       ↑
       |
DashboardComponent

They can access the same root-provided service instance in the normal root-injector scenario.

**Code example**

@Injectable({
  providedIn: 'root'
})
export class MemberService {

}

Then:

export class MemberComponent {

  constructor(
    private memberService: MemberService
  ) {}

}

No manual module provider registration is needed for this root-provided service.

**Interview answer**
providedIn: 'root' registers the service with Angular's root injector. This makes the service available throughout the application and, under the root injector, normally results in one shared service instance for the application. It also supports tree-shakable provider configuration.

**Common mistake**
❌ Saying:
providedIn: 'root' means the service is always globally available in every Angular context.
More precisely, it registers the service with the root injector. Angular has a hierarchical dependency injection system, so a component or feature can also have a more local provider that creates a different instance within that injector scope.

⭐ Important Interview Connection

These concepts are strongly connected:

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

And:

Component
    ↓
Template
    ↓
Data Binding
    ├── Interpolation
    ├── Property Binding
    ├── Event Binding
    └── Two-Way Binding

And:

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

And:

Template
    ↓
Pipe
    ↓
Display Transformation

⭐ 4-Year Experience Scenario

**Interviewer:**
Your MemberComponent currently contains 500 lines of code. It makes HTTP calls, handles UI events, performs formatting, and contains authentication logic. What would you change?

Good answer:

I would separate responsibilities. The component should primarily handle UI-related state and interactions. I would move API communication into services, use Angular's dependency injection to inject those services, use pipes for presentation formatting, and use appropriate reusable components/directives where required. Authentication-related functionality can be handled through a dedicated authentication service and, where appropriate, HTTP interceptors or route guards.

Architecture:

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

This improves:
Maintainability
Testability
Reusability
Separation of concerns
Readability

⭐ Quick Revision Table

Concept
Main Purpose

Example

Interpolation
Display component data
{{ name }}

Property Binding
Component → UI property
[disabled]="isSaving"

Event Binding
UI event → component
(click)="save()"

Two-Way Binding
Component ↔ UI
[(ngModel)]="name"

ngModel
Form control binding
[(ngModel)]="name"

Directive
Add behavior/structure
ngClass,ngStyle

Structural Directive
Change view structure
*ngIf, *ngFor

Attribute Directive
Change behavior/style
ngClass, ngStyle

*ngIf
Conditional view
*ngIf="isActive"

*ngFor
Iterate collection
*ngFor="let m of members"

ngClass
Dynamic CSS classes
[ngClass]="classes"

ngStyle
Dynamic inline styles
[ngStyle]="styles"

Pipe
Transform display data
{{ date | date }}

Custom Pipe
Custom transformation
membershipStatus

Pure Pipe
Runs based on input/args changes
Default

Impure Pipe
Can run every change detection cycle

pure: false
DI
Provides dependencies
Inject MemberService

Service
Reusable application logic

MemberService

@Injectable

DI metadata

@Injectable()

providedIn: 'root'

Root injector registration

Application-wide service

**⭐ One-Line Interview Revision**

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

**⚠️ Modern Angular Interview Note**

For a 4-year Angular interview, don't study only the older syntax.

You should recognize both:

Traditional syntax

<div *ngIf="isActive">
    Active
</div>

<div *ngFor="let member of members">
    {{ member.name }}
</div>

Modern Angular control flow

@if (isActive) {
    <div>Active</div>
}

@for (member of members; track member.id) {
    <div>{{ member.name }}</div>
}

Similarly, understand that modern Angular supports standalone components, so NgModule and AppModule are important concepts to understand, but they are no longer mandatory for every Angular application.

For your interviews, be comfortable explaining why a project uses either approach rather than simply memorizing syntax.
