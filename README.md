# Flex and Grid

Gist - [Flex | Grid](https://gist.github.com/subrotoice/128411f202c40fd35346d6995102c109) <br >
https://github.com/subrotoice/flex-grid <br >
https://css-tricks.com/snippets/css/a-guide-to-flexbox <br >
https://css-tricks.com/snippets/css/complete-guide-grid <br >
https://www.youtube.com/watch?v=kRS5ficucNM <br >
https://www.youtube.com/watch?v=18VLSXfsj94 (Best: Where to use Flex & Grid)

## Flex

```css
.container {
  display: flex;
  flex-direction: row | row-reverse | column | column-reverse;
  flex-wrap: nowrap | wrap | wrap-reverse;
  flex-flow: column wrap; // shorthand: flex-direction and flex-wrap

  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}

The flex item properties: order, flex-grow, flex-shrink, flex-basis, flex, align-self
The flex container properties: flex-direction, flex-wrap, flex-flow, justify-content, align-items, align-content

.item {
  order: 2; /* default is 0 */ jader order nay tara 0 so tara age cole asbe
  Sizing Items:
  flex-basis: the initial size of a flex item
  flex-grow: the growth factor
  flex-shrink: the shrink factor

  flex-grow: 1; /* default 0 */ min-width thakle content space onujayi barbe, Kono item e value 3 thakle onno item theke 3 times barbe
  flex-shrink: 0; /* default 1 */ coto hobe ki na
  flex-basis: 100px; /* default auto */ min-width er poriborte use kora valo

  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ] // shorthand for flex-grow, flex-shrink and flex-basis combined
  NB: It is recommended that you use this shorthand property rather than set the individual properties. The shorthand sets the other values intelligently.
}

* { box-sizing: border-box; } // margin, padding er jonno content baire gele, https://www.w3schools.com/css/tryit.asp?filename=trycss3_box-sizing_new
```

## Grid --- https://prnt.sc/7fxv77ak50YY

```css
.grid-container {
  display: grid;
  grid-template-columns: 100px auto 100px;
  grid-template-columns: 1fr 2fr;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-template: repeat(2, 1fr) / repeat(3, 1fr);  // Shorthand rows/columns
  grid-column-gap: 5px;
  grid-row-gap: 2px;
  grid-gap: 5px;  // Shorthand row & column gap
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
    ". f f f f f f f f f f .";
}

.header {
  background-color: #55efc4;
  grid-area: h;
}

.grid-container { // for responsive | https://youtu.be/kEFIdXzQXYw?t=2062
  display: grid;
  /* grid-template-columns: repeat(auto-fit, 100px); */ // Ager theke bole dibo na koyta colom hobe | minimum width: 100px hobe,
  minimum width: 100px hobe, jayga pele seta extend korbe
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr)); // Auto-fit dile kichu place last e blank theke tar jonno, https://github.com/subrotoice/flex-grid/blob/master/grid_10element.html
  grid-template-rows: repeat(2, 1fr);
}

NB: Grid 2 dimentional overall page structure er jonno valo, Grid normally x axis er jonno. kono section er modde valo
```

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

<!-- CONTACT -->

## Contact

Subroto Biswas - [subrotoiu@gmail.com](mailto:subrotoiu@gmail.com)
