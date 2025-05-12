1. #### ng-template vs ng-container
    - `ng-template`:
        - It is used to define a template that is not rendered directly in the `DOM`.
        - It will only be displayed when a condition is met (e.g., using `*ngIf` or `*ngFor`).
        - It does not appear in the `DOM` unless activated.
    - `ng-container`:
        - It is a virtual element that does not create an extra tag in the `DOM`.
        - Used to group multiple elements without affecting the structure of the `DOM`.
            - Suitable for applying directives like `*ngIf` and `*ngFor`
 
1. #### pure pipe vs impure pipe
    - `Pure Pipe`: Called only when the input value changes (default behavior).
    - `Impure Pipe`: Called on every change detection cycle, regardless of input changes.

1. #### Annotation vs Decorator
    - `Annotation`: Provides metadata about a class or variable `@Input()`, `@Output()`, ... .
    - `Decorator`: A function that adds behavior or functionality to a class, method, or variable `@Component({ })`, `@Directive({ })`.

1. #### Observable vs Promise 
    -  Both handle asynchronous operations, but Promises deal with a single event and are non-cancelable, while Observables handle streams, can emit multiple values, and are cancelable.

1. #### ViewChild VS ContentChild
    - `ViewChild`: Used to access elements inside the component.
    - `ContentChild`: Used to access elements inside `<ng-content>`.

1. #### Unit Test ( Jasmine , Karma  )
    - In Angular, unit testing is done using the `Jasmine` framework for writing test assertions and `Karma` for running the tests.

1. #### type of Subject in Rxjs
    - `Subject`: Subscribers receive new values after subscribing but do not get the last emitted value.
    - `BehaviorSubject`: New subscribers immediately receive the last emitted value or the initial value.
    - `ReplaySubject`: New subscribers immediately receive all previously emitted values.
    - `AsyncSubject`: Only after completion, the last emitted value is sent to all subscribers

1. #### important operators in Rxjs
    - `MergeMap / FlatMap`: Requests are sent simultaneously, and the order doesn't matter; the result is returned when each one finishes.
    - `ConcatMap`: Requests are sent serially (one after another), maintaining the order of completion.
    - `SwitchMap`:When a new request arrives, the previous one is canceled, and the latest one is handled (e.g., useful for search input).
    - `ExhaustMap`:Only the first request is handled, and any subsequent requests are ignored until the first one completes.