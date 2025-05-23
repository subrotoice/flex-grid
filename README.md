# Flex and Grid

1. Gist - [Flex | Grid](https://gist.github.com/subrotoice/128411f202c40fd35346d6995102c109) <br >
2. [subrotoice/flex-grid](https://github.com/subrotoice/flex-grid) <br >
3. [css-tricks:Flex](https://css-tricks.com/snippets/css/a-guide-to-flexbox) <br >
4. [css-tricks:Grid](https://css-tricks.com/snippets/css/complete-guide-grid) <br >
5. [Where to use Flex & Grid](https://www.youtube.com/watch?v=18VLSXfsj94) (Best: Where to use Flex & Grid)

# Ch-1: Flex

```css
.container {
  display: flex;
  flex-direction: row | row-reverse | column | column-reverse;
  flex-wrap: nowrap | wrap | wrap-reverse;
  flex-flow: column wrap;   /* same: flex-direction:column; flex-wrap: wrap; */
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}

.item {
  align-self: flex-start|flex-end; /*Push item to the tor/bottom*/
  order: 2; /* default is 0 */ jader order nay tara 0 so tara age cole asbe
  flex-grow: 1; /* default 0 */ min-width thakle content space onujayi barbe, Kono item e value 3 thakle onno item theke 3 times barbe
  flex-shrink: 0; /* default 1 */ coto hobe ki na
  flex-basis: 100px; /* default auto */ min-width er poriborte use kora valo
  flex: 'flex-grow'|'flex-shrink'|'flex-basis'; /* flex: 1, flex-shrink and flex-basis combined */
}
```

NB: Recommended to use this shorthand property rather than set the individual properties. The shorthand sets the other values intelligently. <br >
NB: Normally use justify-content and align-items. When flex has multiple line and wrap content then align-content comes into play and its values are near to same as justify-content. <br >

Flex container properties: flex-direction, flex-wrap, flex-flow, justify-content, align-items, align-content <br >
Flex item properties: align-self, order, flex-grow, flex-shrink, flex-basis, flex <br >

- { box-sizing: border-box; } // margin, padding er jonno content baire gele, [Box-Sizing](https://www.w3schools.com/css/tryit.asp?filename=trycss3_box-sizing_new)

## What `flex: 1` Means:

```css
flex: 1;
```

is shorthand for:

```css
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0%;
```

### Meaning:

- `flex-grow: 1` → The item **will grow** to take up any available space, proportionally.
- `flex-shrink: 1` → The item **can shrink** if needed.
- `flex-basis: 0%` → The **initial size** of the item is `0`, and the rest is based on available space.

---

## When to Use `flex: 1`

Use `flex: 1` when:

- You want an item to grow and fill space **equally** with other `flex: 1` items.
- You want to build fluid layouts (like sidebars, content areas, etc.).

---

# Ch-2: Grid | [See](https://prnt.sc/7fxv77ak50YY) | [Crome Dev](https://prnt.sc/sWz_wwmrHCov)

```css
.grid-container {
  display: grid;
  grid-template-columns: 100px 100px 100px | repeat(3, 100px) | 100px auto 100px | 1fr 2fr | repeat(3, 1fr); /* All generate 3 columns in different way */
  grid-template-rows: repeat(2, 1fr);
  grid-template: repeat(2, 1fr) / repeat(3, 1fr);  /* Shorthand rows/columns */
  gap: 2px 5px | 5px; /* Shorthand row & column gap */
  justify-items: center; /* align item inside grid cell */
  align-items: center;
  justify-content: center; /* Align entier grid in block level */
  align-content: center;
}

.header {
  grid-column-start: 1;
  grid-column-end: 3;
  grid-column: 1 / 3; // Shorthand of above
  grid-column: 1 / span 2; start 1 and span next 2 grid
  grid-column: 2 /-1; // start 2 and end to last
}

.grid-container { // another way using template-area
  display: grid;
  grid-template-columns: repeat(12, 1fr); // 12 coloums
  grid-template-rows: 100px 1fr 100px;
  grid-template-areas:
    "h h h h h h h h h h h h"
    "m m m m c c c c c c c c"
    ". f f f f f f f f f f ."; /* . means blank cell */
  grid-template-areas:  /* another example */
    "header header"
    "side   main"
    "footer footer";
}

.header {
  background-color: #55efc4;
  grid-area: h; /* no quote here like ' ' 0r " " */
}

.grid-container { /*for responsive | https://youtu.be/kEFIdXzQXYw?t=2062 */
  display: grid;
  /* grid-template-columns: repeat(auto-fit, 100px); */ // Ager theke bole dibo na koyta colom hobe | minimum width: 100px hobe,
  minimum width: 100px hobe, jayga pele seta extend korbe
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  /* Auto-fit dile kichu place last e blank theke tar jonno, https://github.com/subrotoice/flex-grid/blob/master/grid_10element.html */
  grid-template-rows: repeat(2, 1fr);
}
```

Flex: Shape your Layout by Content <br>
Grid: Shape your Content by Layout

# Tailwind Responsive Grid

1. [YouTube](https://www.youtube.com/watch?v=b-hrxkgkG-s) - [play.tailwindcss.com](https://play.tailwindcss.com/9IEjFauwTF)
2. [YouTube](https://www.youtube.com/watch?v=WJDw1J7FZnE) - [play.tailwindcss.com](https://play.tailwindcss.com/Gnn3B6nBx5)

```html
<!-- tailwind.html -->
<!-- https://play.tailwindcss.com/9IEjFauwTF -->
<div class="grid place-items-center p-4">
  <div class="grid max-w-6xl sm:grid-cols-2 gap-4 md:grid-cols-4">
    <h1
      class="text-4xl font-extrabold sm:grid sm:grid-cols-2 sm:col-span-2 sm:gap-4 md:col-span-3"
    >
      <span class="sm:col-span-1 md:col-span-2 bg-orange-200"
        >Grid layout with Tailwind CSS.</span
      >
    </h1>
    <p class="sm:row-start-2 sm:col-start-2 md:col-span-2 md:self-center">
      Lorem, ipsum dolor sit amet consectetur adipisicing elit. Distinctio hic
      itaque alias officiis.
    </p>
    <div class="h-16 bg-blue-500 md:h-32"></div>
    <div class="h-16 bg-blue-500 md:h-32"></div>
    <div class="h-16 bg-pink-500 md:h-32"></div>
    <div class="h-16 bg-blue-500 md:col-start-2 md:h-32"></div>
    <div class="h-16 bg-pink-500 md:h-32"></div>
    <div class="h-16 bg-blue-500 md:h-32"></div>
    <div class="h-16 bg-blue-500 md:h-32"></div>
    <div class="h-16 bg-pink-500 md:h-32"></div>
    <p class="md:self-center">
      Lorem ipsum dolor, sit amet consectetur adipisicing elit, and some more.
    </p>
  </div>
</div>
```

## Make a page full screen height [https://prnt.sc/PRnMjOa14CX\_](https://prnt.sc/PRnMjOa14CX_)

```
grid grid-rows-[auto_1fr_auto] h-screen
```

## Make a page full screen height [https://prnt.sc/PRnMjOa14CX\_](https://prnt.sc/PRnMjOa14CX_)

```html
<div class="max-w-6xl mx-auto">
  <!-- Content here -->
</div>
```

<!-- CONTACT -->

## Contact

Subroto Biswas - [subrotoiu@gmail.com](mailto:subrotoiu@gmail.com)
