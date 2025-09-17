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

1️⃣ Sizes & Units

16px => 1rem => 4 tailwind

w-{number}, h-{number}, p-{number}, m-{number}, gap-{number}

`  p-4  `

2️⃣ Colors & Opacity

text-{color}, bg-{color}, border-{color}, ring-{color}

`  text-red-500, bg-blue-200  `

Opacity: {color}-500/50 or opacity-{number}

`  bg-red-500/30, opacity-75  `

3️⃣ Interactive States

hover:{class}, focus:{class}, active:{class}, visited:{class}

`  hover:text-red-500, focus:bg-blue-200  `

4️⃣ Flexbox & Grid

flex, inline-flex, flex-row, flex-col, flex-wrap

justify-{start|center|end|between|around|evenly}

items-{start|center|end|stretch}

gap-{number}, space-x-{number}, space-y-{number}

Grid: grid, grid-cols-{number}, grid-rows-{number}, place-items-{center|start|stretch}

5️⃣ Typography

text-{size}, font-{weight}, tracking-{number}, leading-{number}

truncate, overflow-ellipsis, whitespace-nowrap

Text color + states: text-{color}, hover:text-{color}

6️⃣ Border & Shadow

border-{size}, border-{color}, rounded-{size}, rounded-{side}-{size}

Shadow: shadow-sm, shadow-lg, shadow-{color}

Ring: ring-{size}, ring-offset-{size}, ring-{color}, ring-opacity-{number}

7️⃣ Position & Z-Index

relative, absolute, fixed, sticky

top-{number}, right-{number}, bottom-{number}, left-{number}

z-{number}

8️⃣ Overflow & Resize

overflow-{auto|hidden|visible|scroll}, overflow-x-{value}, overflow-y-{value}

resize-{none|x|y|both}

9️⃣ Transform & Animation

scale-{number}, rotate-{number}, translate-x-{number}, translate-y-{number}, skew-x-{number}, skew-y-{number}

Animation: animate-spin, animate-ping, animate-bounce, animate-pulse

🔟 Backdrop & Filter

backdrop-blur-{size}, backdrop-brightness-{number}, backdrop-contrast-{number}, backdrop-grayscale

filter, blur-{size}, brightness-{number}, contrast-{number}, saturate-{number}, hue-rotate-{deg}

1️⃣1️⃣ Blend Modes

mix-blend-normal, mix-blend-multiply, mix-blend-screen, mix-blend-overlay, mix-blend-darken, mix-blend-lighten, mix-blend-color-dodge, mix-blend-color-burn, mix-blend-hard-light, mix-blend-soft-light, mix-blend-difference, mix-blend-exclusion, mix-blend-hue, mix-blend-saturation, mix-blend-color, mix-blend-luminosity

1️⃣2️⃣ Responsive & Dark Mode

sm:, md:, lg:, xl:, 2xl:

dark:

`  md:text-lg, dark:bg-gray-800  `

1️⃣3️⃣ Pseudo-class Combination

hover:focus:, focus-visible:

`  hover:focus:text-red-500  `

1️⃣4️⃣ Important

! prefix to override

`  !text-red-500  `

1️⃣5️⃣ Arbitrary Values

w-[23px], bg-[#ff0000], mt-[7px]

1️⃣6️⃣ Aspect Ratio

aspect-auto, aspect-square, aspect-video

1️⃣7️⃣ Z-Index, Opacity, Cursor

z-{number}, opacity-{number}, cursor-{pointer|default|text|move}

1️⃣8️⃣ Place & Align Items

place-items-{center|start|end|stretch}, place-content-{center|start|end|between|around|evenly}

place-self-{auto|center|start|end|stretch}

1️⃣9️⃣ Miscellaneous

overflow-clip, scroll-snap-*, snap-start|end|center

pointer-events-none|auto, select-none|text|all|auto