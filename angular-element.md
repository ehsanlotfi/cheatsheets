```
npm i @angular/elements --save
```

```
@Component({
  template: '<h1>HTML Template Test</h1>',
  encapsulation: ViewEncapsulation.ShadowDom
})
export class HTMLTemplateComponent {
}
```

```
export class AppModule {

  constructor(private injector: Injector) { }

  ngDoBootstrap() {
    const el = createCustomElement(HTMLTemplateComponent, {
      injector: this.injector
    });
    customElements.define('html-template-tag', el);
  }
  
 }
```
###### create build-elements.js file in root project
```
const fs = require('fs-extra');
const concat = require('concat');

(async function build() {
    const files = [
        './dist/web-component/runtime.js',
        './dist/web-component/polyfills.js',
        './dist/web-component/scripts.js',
        './dist/web-component/main.js',
    ];

    await fs.ensureDir('elements');
    await concat(files, 'elements/web-component-file.js');
})();

```
```
"build:elements": "ng build --prod --output-hashing none && node build-elements.js"
```
