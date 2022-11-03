## Tailwind CSS Cheat Sheet

### Basic definitions
- Utility first css framework
- Rapidly build custom design
- Highly customizable
- Low level framework
- No pre built components
- Building block full creative components
- Minimal custom css
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
