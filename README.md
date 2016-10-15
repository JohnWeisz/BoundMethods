# BoundMethods

Transparent method binding in TypeScript to persist the lexical scope of `this`. Usage: add the `@bound` decorator to methods.

```ts
class Foo {
    private foo = "hello, foo";

    @bound public bar() {
        console.log(this.foo);
    }
}

var foo = new Foo();

setTimeout(foo.bar, 500); // "hello, foo"
```

## How it Works

Using `@bound` on an instance method will override the PropertyDescriptor of that method with a getter, that injects a bound version of the method into the instance object on the first invocation. Subsequent calls will use the method on the instance object, effectively hiding the original unbound method on the prototype object. The side-effect of this is that modifications to the prototype method will not take effect.

Using `@bound` on a static method will simply override it with a bound version on the constructor function itself.
