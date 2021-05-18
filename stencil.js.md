#### ☑ basic usage
```
import { Component, Prop } from '@stencil/core';

@Component({
  tag: 'sample-text'
})
export class SampleText {

 @Prop() text: string;

  render() {
    return (
        <h1>Sample {this.text}</h1>
        <section><slot /></section>
    );
  }
}
```
```
  <sample-text text="hello world!"></sample-text>
```

#### ☑ Decorators
|Name|Desc|Params|Persian desc|
|-|-|-|-|
|@Component()|new web component|aaaa|aaaa|
|@Prop()|exposed property/attribute|aaaa|aaaa|
|@State()|internal state of the component|aaaa|aaaa|
|@Watch()|hook that runs when a property or state changes|aaaa|aaaa|
|@Element()| reference to the host element|aaaa|aaaa|
|@Method()| exposed public method|aaaa|aaaa|
|@Event()|DOM event the component might emit|aaaa|aaaa|
|@Listen()|listens for DOM events|aaaa|aaaa|


