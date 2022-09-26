## 🤿 Introduction to Dependency Injection

Let me start with an analogy explaining what exactly DI is!

Imagine you need to go to work today. Think of all the things you need. 
* *Clothes* - You have shirts in your closet. You don't bother about the details of how that shirt was created. You pick one. 
* *Car* - You might drive to work. You don't know how your car was designed or created.

You are a component depending on external things like clothes, car in order to go to work. You know how to use it but don't know how it was built.

Dependency Injection is an integral part of the Angular framework. Classes with Angular Decorators like Components, Directives, Pipes, and Injectables can configure their dependencies. They just know how to use their dependencies and don't know how the dependencies were created.

> Dependency Injection or DI is a design pattern in which a class requests dependencies from external sources rather than creating them.

### How are these dependencies provided to the consumers?

Injector is responsible for instantiating the dependency and injecting it into the component or service. When a dependency is requested, the injector verifies its list of dependencies. If an instance already exists, the injector returns the same. If not, a new instance is created and stored in the list of dependencies.

A class can be made available for Dependency injection by adding the decorator @ Injectable . `providedIn: root` signifies a singleton instance of the service.

```
@Injectable({
  providedIn: 'root'
})
class UserService {}
```
Components inject the dependencies in their constructor. 
```
@Component({ … })
class UserComponent {
  constructor(private service: UserService) {}
}
```

When the injector resolves all the dependencies, it returns the instance as arguments of the component's constructor. 

-----
## Thanks for reading!

The next article will be in-depth about the injectors in Angular. 
 

Please feel free to reach out on [Twitter](https://twitter.com/@devminibhati) or [LinkedIn](https://www.linkedin.com/in/minibhati93/)