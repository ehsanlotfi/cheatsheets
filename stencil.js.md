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
|Name|Desc|Persian desc|
|-|-|-|
|```<slot />```|Display content added to the component ||

#### ☑ Decorators
|Name|Desc|Params|Persian desc|
|-|-|-|-|
|@Component()|new web component|||
|@Prop()|exposed property/attribute|||
|@State()|internal state of the component|||
|@Watch()|hook that runs when a property or state changes|||
|@Element()| reference to the host element|||
|@Method()| exposed public method|||
|@Event()|DOM event the component might emit|||
|@Listen()|listens for DOM events|||

#### ☑ Lifecycle
|Name|Desc|Persian desc|
|-|-|-|-|
| ```connectedCallback()	 ```|||
| ```disconnectedCallback()	 ```|||
| ```componentWillLoad()	 ```|||
| ```componentDidLoad()		 ```|||
| ```componentShouldUpdate() ```|||
| ```componentWillRender()	 ```|||
| ```componentDidRender()	 ```|||
| ```componentWillUpdate()	 ```|||
| ```componentDidUpdate()    ```|||



### ☑ Example
#### ☑ slot
```
<my-component>
  <p slot='my-header'>Hello</p>
  <p slot='my-footer'>Thanks</p>
</my-component>
```
```
render () {
  return <div>
    <header><slot name='my-header' /></header>
    <footer><slot name='my-footer' /></footer>
  </div>
}
```

