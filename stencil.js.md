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

#### ☑ Special Tags
|Name|Desc|Params|Persian desc|
|-|-|-|-|
|<slot />|Display content added to the component |____|____|

#### ☑ Decorators
|Name|Desc|Params|Persian desc|
|-|-|-|-|
|@Component()|new web component|____|____|
|@Prop()|exposed property/attribute|____|____|
|@State()|internal state of the component|____|____|
|@Watch()|hook that runs when a property or state changes|____|____|
|@Element()| reference to the host element|aaaa|aaaa|
|@Method()| exposed public method|____|____|
|@Event()|DOM event the component might emit|____|____|
|@Listen()|listens for DOM events|____|____|


