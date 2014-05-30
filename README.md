## WFF (Waiting For Flexbox)

WFF is an old-fashioned grid system built with Sass, the child of "old-school" css grids and new semantic ones. Based on a massive @extend logic, it has been designed to have a small footprint on relatively large projects.

## Requirements

- Sass 3.3+

## Availables functions

**default-layout($map)**

Override the default internal layout.
You can set a lot of paramater, like:
- math (fluid or static - convert to %, or conserve the unit)
- width (in px, em… - width of the container)
- columns (a unitless number - the number of columns)
- gutter (a number, with same unit as width - size of a gutter)
- external (boolean - if fluid, this add fake external gutters on the container)

```sass
@import "scss/wff";

// Override the default internal layout
$my-layout: default-layout((width: 60em, columns: 10, gutter: 3em));
// The internal layout is now (math: fluid, width: 60em, columns: 10, gutter: 3em, external: false)

@include placeholders;
```

**layout($map)**

Create a new layout.

Same paramaters as default-layout($map).

```sass
@import "scss/wff";

// Override the default internal layout
$my-layout: default-layout((columns: 10));
$larger: layout((columns: 6));

@include placeholders;

// Here we have 10 columns

@breakpoint('screen and (min-width: 64em)', $larger) {
    // Here we have 6 columns
}
```

## Availables mixins

**placeholders()**

```sass
@import "scss/wff";

// We need to include placeholders once, because all your grid related CSS will go here
@include placeholders;
```

**container($position: center)**

$position: left / center / right

```sass
@import "scss/wff";

@include placeholders;

.container {
    @include container(left);
}
```

**column($size: 1, $position: false)**

$size: unitless number

$position: false / shift number / last

```sass
@import "scss/wff";

@include placeholders;

.container {
    @include container;
}

.first {
    @include column;
}

.second {
    @include column(2, shift 3);
}

.third {
    @include column(3, last);
}
```

**span($size: 1, $position: false)**

$size: unitless number

$position: false / shift number / last

```sass
@import "scss/wff";

@include placeholders;

.container {
    @include container;
}

.first {
    @include span;
}

.second {
    @include span(2, shift 3);
}

.third {
    @include span(3, last);
}
```

**column-gallery($size: 1, $unset: 0)**

$size: unitless number

$unset: unitless number

```sass
@import "scss/wff";

@include placeholders;

.container {
    @include container;
}

.product {
    @include column-gallery;
}
```

**span-gallery($size: 1, $unset: 0)**

$size: unitless number

$unset: unitless number

```sass
@import "scss/wff";

@include placeholders;

.container {
    @include container;
}

.product {
    @include span-gallery;
}
```

**clearfix()**

```sass
@import "scss/wff";

@include placeholders;

.container {
    @include container;
}

.row {
    @include clearfix;
}
```
