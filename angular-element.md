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
##### ⚠ Add your component to entryComponents and comment bootstrap: [AppComponent] line
###### create build-elements.js file in root project
```
npm i fs-extra --save
npm i concat --save
```
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
const fs = require('fs-extra');
const concat = require('concat');

(async function build() {
    await fs.ensureDir('elements');
    const es5 = ['./dist/test-sample/runtime-es5.js','./dist/test-sample/polyfills-es5.js','./dist/test-sample/main-es5.js'];
    const es2015= ['./dist/test-sample/runtime-es2015.js','./dist/test-sample/polyfills-es2015.js','./dist/test-sample/main-es2015.js'];
    await concat(es5, 'elements/exir-header-web-component-es5.js');
    await concat(es2015, 'elements/exir-header-web-component.js');
})();
```

```
"build:elements": "ng build --prod --output-hashing none && node build-elements.js"
```
