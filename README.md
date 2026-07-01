# dev-spring-boot

https://www.udemy.com/course/spring-hibernate-tutorial/learn/lecture/36829934#overview

## Notes

### Section 2: Spring Core

#### Injection Types - Which one to use?

- Constructor injection
- Use this when you have required dependencies (generally recommended by spring.io development team as first choice)

- Setter injection
- Use this when you have optional dependencies, if dependency is not provided, your app can provide reasonable default logic

#### Qualifiers / Primary
- When multiple implementations of an interface exist, Spring can't resolve which bean to inject and throws `NoUniqueBeanDefinitionException`
- `@Qualifier` — specify exactly which implementation to inject by bean name
  - Annotate at the injection point (constructor param, setter, or field)
  - Bean name defaults to the class name with the first letter lowercased (e.g. `CricketCoach` → `cricketCoach`)
- `@Primary` — mark one implementation as the default choice when no qualifier is given
  - Only one bean per type may be marked `@Primary` (multiple defeats the purpose and errors out)

##### Qualifier vs. Primary — which to use?
- `@Primary` lets the *bean* declare itself the default — one decision, applied everywhere
- `@Qualifier` lets the *injection point* choose — more specific, decided per use
- If both are present, `@Qualifier` wins (specific beats general)
- Prefer `@Qualifier` when you need explicit control; prefer `@Primary` for a sensible app-wide default

#### Bean Scopes
- scope refers to bean's lifecycle
- Default scope is singleton
  - Creates only one instance of the bean by default
- Explicitly specify Bean Scope
  - singleton
  - prototype
  - request
  - session
  - application
  - websocket 
