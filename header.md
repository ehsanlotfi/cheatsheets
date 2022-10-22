### main.ts
```
var interValModule = setInterval(() => {
  if ((window as any).headerLoaded && (window as any).headerLoaded) {
    platformBrowserDynamic().bootstrapModule(AppModule)
      .catch(err => console.error(err));
    clearInterval(interValModule);
  }
}, 100);
```

### index.html
```
  <script>
    window["clientId"] = "map";
    window["clientRoot"] = document.getElementsByTagName("base")[0].href;
    var script = document.createElement('script');
    script.setAttribute('rel', 'preload');
    script.setAttribute('src', `https://cdn.sata${(location.origin.includes("sata86") || location.origin.includes("localhost")) ? "86" : ""}.sys/web-components/exir-header-web-component.js`);
    document.head.appendChild(script);
  </script>
```

### app.module.ts
```
@NgModule({
  declarations: [],
  imports: [
    TranslateModule.forRoot(translateModuleConfig),
  ],
  schemas: [CUSTOM_ELEMENTS_SCHEMA],
})
export class AppModule {

 constructor(
    private zone: NgZone,
    private permissionsService: NgxPermissionsService,
    private readonly tSvc: TranslateService) {
    (window as any)["onChangeLang"] =  (lang) => {
      this.zone.run(async () => {
        await this.tSvc.use(lang.translate).toPromise();
      });
    };
    this.permissionsService.addPermission(window["permissionsList"]);
  }
}
```


### app.componenet.ts
```
<exir-header-web-component name=""></exir-header-web-component>
```
