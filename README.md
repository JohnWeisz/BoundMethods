# BoundMethods

Transparent method binding in TypeScript to persist the lexical scope of `this`.

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
