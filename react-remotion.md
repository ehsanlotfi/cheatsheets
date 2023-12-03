  گرفتن فریم جاری
  ```
  const frame = useCurrentFrame();
  ```
 
اطلاعات تنظیم شده برای ویدیو
  ```
  const { fps, durationInFrames, width, height } = useVideoConfig();
  ```

باکس اصلی ویدیو ها میتوان به دو شکل تعریف شود
   ```
   <Composition /> 
   <Still />
   ```

انیمیشن ها
  ```
  spring, interpolate

  ```

استفاده مجدد از یک کامپوننت در فریم های مختلف
   ```
   <Sequence></Sequence>
   ```

 فایل های assets را در پوشه public بریزید و توسط staticFile به آن دسترسی دارید
  ```
  <Img src={staticFile("logo.png")} />
  <Img src={staticFile(`/${frame}.png`)} />;
  <Video src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" />
  <Audio src={staticFile("tune.mp3")} />;
  ```
