#### ☑ getting started
```
npm install -g stencil
```
```
npm init stencil
```
We want to build a reusable component so we will choose the third option, **component**.


#### ☑ basic usage
```
{ Component, Host, h, Prop, State } from '@stencil/core';

@Component({
  tag: 'sample-text'
})
export class SampleText {

 @Prop() text: string;
 @State() validFlag: string;

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
|@Element()| reference to the host element||<p dir='rtl' style='font-size: 10px;' align='right'>برای دسترسی به المنت های تعریف شده داخل کامپوننت ستفاده میشود  برای دسترسی به shadowDOM از shadowRoot استفاده میکنیم</p>|
|@Method()| exposed public method||<p dir='rtl' style='font-size: 10px;'  align='right'>فراخوانی متد از بیرون بوسیله انتخابگر المنت</p>|
|@Event()|DOM event the component might emit|||
|@Listen()|listens for DOM events|||

#### ☑ Lifecycle
|Name|Desc|Persian desc|
|-|-|-|
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

