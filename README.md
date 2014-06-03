## WFF (Waiting For Flexbox)

WFF is an old-fashioned grid system built with Sass, the child of "old-school" css grids and new semantic ones. Based on a massive @extend logic, it has been designed to have a small footprint on relatively large projects. It's also support infinite nesting and column shifting.

## Requirements

- Sass 3.3+

## Another grid system? What's make this one different?

Currently, if you choose a "semantic" grid system and have watched the generated CSS a little, you maybe noticed that your framework generally doesn't respect the "DRY" philosophy.

```sass
// Example using a classic semantic grid system

.first {
  @include column;
}

.second {
  @include column;
}

.third {
  @include column(2);
}
```
```css
.first {
  float: left;
  width: 7.1875%;
  margin-right: 3.125%;
}

.second {
  float: left;
  width: 7.1875%;
  margin-right: 3.125%;
}

.third {
  float: left;
  width: 17.5%;
  margin-right: 3.125%;
}
```

But because WFF use massively Sass @extend, it is able to produce this:

```sass
// Example using wff grid system

@include placeholders;

.first {
  @include column;
}

.second {
  @include column;
}

.third {
  @include column(2);
}
```
```css
.first, .second {
  width: 7.1875%;
}

.third {
  width: 17.5%;
}

.first, .second, .third {
  float: left;
  margin-right: 3.125%;
}
```

Better, no? Check out [https://github.com/Onemore/wff/wiki](documentation) to find more.
