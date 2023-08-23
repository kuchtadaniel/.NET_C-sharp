# Angular Terms and Descriptions

| Term                   | Description                                                                                                  | Example                                                |
|------------------------|--------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| @ContentChild          | A decorator and query function used to access projected content or child components from the parent component. | `@ContentChild(SomeComponent) contentChild: SomeComponent;` |
| @Input                 | A decorator used to declare an input property that allows data to flow into a component from its parent.    | `@Input() value: string;`                             |
| @Output                | A decorator used to declare an output property that allows a component to emit events to its parent.       | `@Output() valueChange = new EventEmitter<string>();` |
| @ViewChild             | A decorator and query function used to access child components or DOM elements from the parent component. | `@ViewChild(SomeComponent) childComponent: SomeComponent;` |
| ActivatedRoute         | A service that provides information about the currently activated route and its parameters.               | `constructor(private route: ActivatedRoute) { }`       |
| ActivatedRouteSnapshot | A snapshot of the route information at the time the guard is called, used for route data access in guards and resolvers. | `routeSnapshot: ActivatedRouteSnapshot;`              |
| Ahead-of-Time (AoT)   | A compilation process that compiles Angular templates and components during the build process, resulting in smaller and faster applications. | `ng build --aot`                                     |
| Angular                | A popular TypeScript-based open-source web application framework developed and maintained by Google.     | Angular is used to build modern web applications.     |
| Angular CLI            | The Angular Command Line Interface, used for creating, building, testing, and deploying Angular applications. | `ng new my-app`                                      |
| Angular Material       | A UI component library for Angular applications, providing pre-styled and feature-rich UI elements.     | `import { MatButtonModule } from '@angular/material';` |
| Animations             | Transition effects using triggers                                                                       | Use `[@triggerName]` to animate changes.             |
| Async Pipe             | Subscribe to observables                                                                                 | `{{ data$ | async }}`                                |
| Attribute Directives   | Directives that modify the behavior or appearance of an element's existing behavior.                     | `[appHighlight]="'yellow'"`                         |
| Binding                | Connecting component data to the template to keep them in sync. Types include Interpolation, Property Binding, and Event Binding. | `<h1>{{ title }}</h1>`                                |
| Bootstrap Module       | The root module of an Angular application, used to bootstrap the initial component and start the application. | `@NgModule({ bootstrap: [AppComponent] })`           |
| CanActivate            | A route guard interface that checks if a route can be activated before navigating to it.                 | `canActivate: [AuthGuard]`                          |
| CanDeactivate          | A route guard interface that checks if a route can be deactivated before leaving it.                     | `canDeactivate: [CanDeactivateGuard]`              |
| CD Strategy            | Change detection strategy used by Angular to decide when to check for changes and update the view. Strategies include OnPush and Default. | `changeDetection: ChangeDetectionStrategy.OnPush`  |
| Change Detection       | The process by which Angular determines if there have been changes to the application's data and updates the view accordingly. | Angular automatically triggers change detection when data changes. |
| Component              | A building block of an Angular application, encapsulating HTML, CSS, and TypeScript logic.                | `@Component({ selector: 'app-root' })`              |
| Component Interaction  | Parent and child components communicating                                                                 | Using `@Input` and `@Output` for communication.     |
| Component Styles       | Styles applied to Angular components, typically defined using CSS, SCSS, or other styling languages.     | `.my-component { color: blue; }`                     |
| ComponentFixture        | A utility provided by Angular's testing framework for interacting with and testing components.            | `fixture = TestBed.createComponent(MyComponent);`   |
| Content Projection     | The ability to insert content into a component's template from its parent component.                      | `<ng-content></ng-content>`                         |
| ContentChildren        | A decorator and query function used to access projected content or child components from the parent component. | `@ContentChildren(ItemComponent) items: QueryList<ItemComponent>;` |
| Currency Pipe          | A built-in pipe used to format currency values based on locale and currency code.                         | `{{ price | currency: 'USD':true }}`                |
| Data Binding           | A mechanism to establish a connection between the component's data and the view, keeping them in sync.    | `<p>{{ data }}</p>`                                   |
| Date Pipe              | A built-in pipe used to format date values based on locale and formatting options.                       | `{{ date | date: 'medium' }}`                       |
| Decimal Pipe           | Format number with decimal points                                                                         | `{{ number | number: '1.2-2' }}`                    |
| Dependency Injection   | A design pattern where the required dependencies of a component or service are provided from the outside rather than created within the component. | `constructor(private authService: AuthService) { }` |
| Directive              | A marker on the DOM element that tells Angular to do something with that element.                        | `@Directive({ selector: '[appHighlight]' })`        |
| Eager Loading          | Loading a module and its components as soon as the application starts, as opposed to lazy loading.     | Eager loading can improve initial application load time. |
| ElementRef             | A reference to the DOM element of a directive, obtained using dependency injection.                      | `constructor(private el: ElementRef) { }`            |
| Event Binding          | Binding to DOM events in the template to respond to user interactions.                                     | `<button (click)="onClick()">Click me</button>`    |
| FormBuilder           | A service that simplifies the creation of FormGroup and FormControl instances in reactive forms.         | `constructor(private fb: FormBuilder) { }`          |
| HostBinding            | A decorator used to set properties of the host element of a directive.                                    | `@HostBinding('class.active') isActive = true;`     |
| HostListener           | A decorator used to subscribe to events on the host element of a directive.                                | `@HostListener('click', ['$event']) onClick(event: Event) { ... }` |
| Immutability           | The principle of not modifying data directly but instead creating new copies with modifications.          | Using immutability to ensure data consistency.     |
| Input                  | A decorator used to declare an input property that allows data to flow into a component from its parent. | `@Input() count: number;`                            |
| Jasmine                | A popular testing framework used in combination with Karma for writing unit tests in Angular applications. | Writing Jasmine tests for Angular components.      |
| Json Pipe              | Transform object to JSON format                                                                            | `{{ data | json }}`                                 |
| Just-in-Time (JiT)     | The default compilation mode in which Angular compiles templates in the browser at runtime.               | JIT compilation mode provides fast development feedback. |
| Karma                  | A popular test runner used in the Angular ecosystem to execute unit tests.                                | Running Karma to execute unit tests for an Angular app. |
| KeyValue Pipe          | A built-in pipe used to iterate over key-value pairs from objects or Maps.                                | `{{ object | keyvalue }}`                           |
| Lazy Loading           | Loading parts of an application only when they are needed, improving initial load time.                  | Implementing lazy loading for improved performance. |
| Lifecycle Hooks        | Methods provided by Angular that allow developers to perform actions at specific points in a component's lifecycle. Common hooks include ngOnInit, ngOnDestroy, etc. | Implementing `ngOnInit` and other lifecycle hooks. |
| LowerCase Pipe         | A built-in pipe used to transform a string to lowercase.                                                  | `{{ text | lowercase }}`                            |
| Metadata               | Decorator that provides info about a class (@Component, @NgModule)                                        | Using metadata decorators to configure components and modules. |
| Module                 | A container for related components, services, and other code, used to organize the application.          | Creating and configuring modules in Angular.      |
| ng build               | A command in Angular CLI used to build your application for production deployment.                        | Running `ng build` to create a production-ready build. |
| ng lint                | A command in Angular CLI used to analyze and enforce linting rules on your code.                           | Using `ng lint` to ensure code quality.           |
| ng serve               | A command in Angular CLI used to serve your application locally during development.                         | Running `ng serve` for local development and testing. |
| ng test                | A command in Angular CLI used to run unit tests for your application.                                      | Running `ng test` to execute unit tests.           |
| ng-container           | A structural directive that serves as a placeholder for hosting elements and content without adding an extra DOM element. | Using `ng-container` to conditionally render content. |
| ng-content             | A directive used to project content from a parent component into a child component's template.           | Using `ng-content` for content projection.         |
| ngFor                  | A directive used in templates to iterate over a collection and render elements for each item.            | `<div *ngFor="let item of items">{{ item.name }}</div>` |
| ngIf                   | A directive used to conditionally include or exclude elements in the template.                              | `<p *ngIf="showContent">Content is visible</p>`   |
| ngModel                | A directive used to achieve two-way binding for form elements.                                              | `<input [(ngModel)]="username">`                   |
| NgModule               | A decorator used to define a module in Angular, which groups related components, services, and other code. | `@NgModule({ declarations: [AppComponent] })`     |
| NgModules              | Modules in Angular that group related code, including components, services, and directives.               | Organizing code into reusable NgModules.         |
| NgRx                   | State management pattern + library                                                                        | Using NgRx for managing application state.       |
| ngStyle                | A directive used to add or modify inline CSS styles based on condition evaluation.                         | `<div [ngStyle]="{ color: isActive ? 'green' : 'red' }">Text</div>` |
| ngSwitch               | A directive used to conditionally render content based on a given expression.                               | `<div [ngSwitch]="status">...</div>`              |
| Observable             | A data stream that allows asynchronous processing and propagation of changes.                              | `data$: Observable<Data>`                          |
| OnPush Strategy        | A change detection strategy where the view is only updated when inputs to the component change.            | `changeDetection: ChangeDetectionStrategy.OnPush`  |
| Output                 | A decorator used to declare an output property that allows a component to emit events to its parent.       | `@Output() onButtonClick = new EventEmitter<void>();` |
| Percent Pipe           | A built-in pipe used to format number values as percentages.                                                | `{{ percentage | percent }}`                      |
| Pipe                   | A transformation applied to data in a template, used for formatting and displaying data.                    | `{{ data | myCustomPipe }}`                       |
| Property Binding       | Binding to a DOM element's property in the template to set or update its value.                            | `<img [src]="imageUrl" alt="Image">`              |
| Protractor             | An end-to-end testing framework specifically designed for testing Angular applications.                      | Writing end-to-end tests using Protractor.       |
| Providers              | How dependencies are provided in NgModules                                                                 | Providing services using the `providers` array.  |
| Pure Pipes             | Pipes that are stateless and only dependent on the input value, ensuring that they produce the same output for the same input. | Creating pure pipes for efficient transformation. |
| Reactive Forms         | A way to create forms in Angular using reactive programming, where form controls are defined programmatically using FormControl, FormGroup, and FormArray. | Creating reactive forms for user input.           |
| Reactive Programming   | A programming paradigm focused on data flows and the propagation of changes, often used in Angular with RxJS. | Using RxJS for managing asynchronous data flows.  |
| Renderer2              | A service that provides methods to manipulate the DOM in a way that's safe across different rendering engines. | `constructor(private renderer: Renderer2) { }`       |
| Resolver               | A route guard interface that pre-fetches data before activating a route.                                   | `resolve: MyResolverService`                        |
| Root Component         | Bootstrapped component rendered first                                                                       | The root component is typically named `AppComponent`. |
| Route                  | A configuration that defines how to navigate between different views in an Angular application.           | `{ path: 'home', component: HomeComponent }`        |
| Router                 | The module that enables navigation between views/components based on the URL.                             | `constructor(private router: Router) { }`           |
| RouterLink             | A directive used to create navigation links that trigger route changes in the application.                | `<a [routerLink]="['/home']">Home</a>`            |
| RouterOutlet           | A directive used to mark the location where the router will insert the component corresponding to the current route. | `<router-outlet></router-outlet>`                 |
| RouterStateSnapshot    | A snapshot of the router state, including the URL and the activated route at the time the guard is called. | `routeSnapshot: RouterStateSnapshot;`             |
| Routing                | The process of navigating between different views or components based on the URL.                         | Implementing routing to create a single-page application. |
| RxJS                   | A library for reactive programming in JavaScript, used in Angular to work with asynchronous data streams. | Using RxJS for handling asynchronous operations.   |
| Service                | A class used to share data and functionality across components, often used for managing data, communication, etc. | `@Injectable({ providedIn: 'root' })`               |
| Slice Pipe             | A built-in pipe used to extract a portion of a string or an array.                                         | `{{ text | slice: start:end }}`                    |
| Stateful Pipes         | Pipes that maintain internal state and depend on both the input and the state.                            | `{{ data | customPipe }}`                          |
| Structural Directives  | Add/remove elements in DOM (*ngFor, *ngIf)                                                                 | Using structural directives for dynamic templates. |
| Template               | The HTML structure that defines the component's view.                                                      | `<div>{{ content }}</div>`                         |
| Template-driven Forms  | A way to create forms in Angular by using directives in the template. Form controls are automatically created based on the DOM structure. | Creating template-driven forms for user input.    |
| TestBed                | A utility provided by Angular's testing framework for configuring and creating instances of components, services, and other dependencies for testing. | Configuring and using TestBed for testing.        |
| TitleCase Pipe         | A built-in pipe used to transform a string to title case.                                                  | `{{ text | titlecase }}`                           |
| Tree Shaking           | Eliminates unused code in build                                                                            | Using tree shaking to reduce bundle size.         |
| Two-Way Binding        | A combination of property binding and event binding, allowing data synchronization between a component and its template. | `<input [(ngModel)]="username">`                  |
| UpperCase Pipe         | A built-in pipe used to transform a string to uppercase.                                                  | `{{ text | uppercase }}`                           |
| View Encapsulation     | A technique to control how styles are scoped within a component's template. Options include Emulated, Native, and None. | `encapsulation: ViewEncapsulation.Emulated`       |
| ViewChildren           | A decorator and query function used to access child components or DOM elements from the parent component. | `@ViewChildren(ItemComponent) items: QueryList<ItemComponent>;` |
| Webpack                | A popular open-source module bundler used in modern web development to bundle assets and code.           | Bundling assets and code using Webpack.           |
| Zone.js                | A library that intercepts and monitors asynchronous operations, often used in Angular to trigger change detection. | Using Zone.js to manage asynchronous tasks.       |
| Zones                  | Execution context to track async tasks   
