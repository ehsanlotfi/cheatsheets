## Tailwind CSS Cheat Sheet

### Basic definitions
- Utility first css framework
- Rapidly build custom design
- Use atomic CSS methodology.
- Highly customizable
- Low level framework
- No pre built components
- Better developer experience
- Mobile first design

### Layout
##### container 
- None	width: 100%;
- sm (640px)	max-width: 640px;
- md (768px)	max-width: 768px;
- lg (1024px)	max-width: 1024px;
- xl (1280px)	max-width: 1280px;
- 2xl (1536px)	max-width: 1536px;

##### columns-{count}  => count = { number[1-12], 3xs-7xl }
```
<div class="columns-3xs ...">
  <img class="w-full aspect-video ..." src="..." />
  <img class="w-full aspect-square ..." src="..." />
  <!-- ... -->
</div>
```
##### break-after-{value} => value = { auto, avoid, all, avoid-page, page, right, column }
##### break-Before-{value} 
##### break-Inside-{value}
```
<div class="columns-2">
  <p>Well, let me tell you something, ...</p>
  <p class="break-inside-avoid-column">Sure, go ahead, laugh...</p>
  <p>Maybe we can live without...</p>
  <p>Look. If you think this is...</p>
</div>
```

##### [🛈](https://www.w3schools.com/cssref/tryit.php?filename=trycss3_box-decoration-break) box-decoration-{value} => value = { clone, slice }

##### aspect-{ratio}  => ratio = { auto, square, video }
```
<iframe class="w-full aspect-video" src="https://www.youtube.com"></iframe>
```

### Sizing
16px => 1rem => 4 tailwindcss
```
<div class="w-4"></div>
```
##### w-{number}, h-{number}, max-w-{number}, min-w-{number}
```
.w-96
.w-80
.w-10

.w-full
.w-screen
.w-fit

...
```
##### w-{fraction}, h-{fraction}, max-w-{fraction}, min-w-{fraction}
```
.w-1/2
.w-2/5
```
