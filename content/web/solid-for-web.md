# SOLID for javascript, typescript, component frameworks

An aproach to solid principles from a javascript perspective and it's aproach nowdays (including it's frameworks)

- The Single Responsibility Principle
- The Open-Closed Principle
- The Liskov Substitution Principle
- The Interface Segregation Principle
- The Dependency Inversion

### References

- [SOLID explained for OOP](https://www.freecodecamp.org/news/solid-principles-explained-in-plain-english/) TODO find new reference, this is baaadly writen
- [Second reference](https://www.youtube.com/watch?v=MSq_DCRxOxw\&t=57s)

## The Single Responsibility Principle

- Each class, module or function. Everything that can encapsulate functionality or information must do one thing. therefore when is change there is only one reason to be changed
- If there are complex methods or modules, you would divide it's responsability in smaller objects or functions
- it's more easier to figure out the location of the problems in the code and spot them in the file. i.e someone works on thing -> problems occures -> most probably it's from that thing or smt links to it

## Open-Closed Principle

- Open for extension and close to modification.
- Use interfaces to enforce a standard on objects, functions and classes, indicate what you want to be used if you want to extend your component, and close it to modification.
- It might be possible to use the same type of component consequently. Anticipate and construct it in such way in that you don't need to modify in multiple places if you want to extend it. Examples:
  - Navigation bar and multiple pages. Must be made in such way when you added a new page navigation bar would take it automatically without changing the navigation comp
  - If you need a Nested Dropdown make it in such way that can be scalled infinitely. Where the links and names can be easely modify without changing the component

## Liskov Substitution Principle

- A class that extends another can use the same methods as the extended class
- Adapt the methods to the new class by overwriting them
- subtype objects should be substitutable for supertype objects
- In case of components, a component can be extended, props defined, and extended component can recieve the same methods as the initial and the addition.
  - You can use the spread operators to deconstruct all props from the inherited component, and `extends React.YourHTMLAttribute<...>` to inherit and enforce the types.

## Interface Segregation Principle

- clients should not depend upon interfaces/apis that they don't use
- components shouldn't depend on props you are not gonna use
- make a new interface for that specific component instead of using an already existing interfaces that has the needed variables atached to the unused ones.

## Dependency Inversion Principle

- one entity should depend upon abstractions not concretions
- tide to OCP
- you can make elements prone to extension and close to modification by passing callbacks for generalities. And inject that dependencie from props, for Examples
  - onSubmit function for a form component
  - a fetch function for a display component and so on
