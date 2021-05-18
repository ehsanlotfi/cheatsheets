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
    );
  }
}
```
```
  <sample-text text="hello world!"></sample-text>
```
