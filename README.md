# SCSS BEM Transition Mixin
SCSS mixin for BEM-element properties transition. Save time writing less code.

## Using

### Simple
```scss
.block {
  @include property-transition(
    "__title",
    (
      transform: translateY(-0.5em)
    )
  );
}
```
Will be:

```css
.block__title {
  transition: transform 0.25s ease;
}
.block:hover .block__title {
  transform: translateY(-0.5em);
}
```

### Changing duration, easing and states
```scss
.block {
  @include property-transition(
    "__title",
    (
      transform: translateY(-0.5em)
    ),
    1s,
    ease-in-out,
    (
      ":hover",
      ":focus",
      ".is-active"
     )
  );
}
```
Will be:

```css
.block__title {
  transition: transform 1s ease-in-out;
}
.block:hover .block__title,
.block:focus .block__title,
.block.is-active .block__title {
  transform: translateY(-0.5em);
}
```

### Grouping elements with individual property easing and duration
```scss
.block {
  @include property-transition(
    (
      "__title",
      "__footer"
    ),
    (
      transform: translateY(-0.5em),
      width: (
        value: 50%,
        duration: 1s,
        easing: ease-in-out
      )
    )
  );
}
```
Will be:

```css
.block__title,
.block__footer {
  transition:
    transform 0.25s ease,
    width 1s ease-in-out;
}
.block:hover .block__title,
.block:hover .block__footer {
  transform: translateY(-0.5em);
  width: 50%;
}
```

### Pseudo and self elements
```scss
.block {
  @include property-transition(
    (
      ":self",
      "::before"
    ),
    (
      color: red
    )
  );
}
```
Will be:

```css
.block,
.block::before {
  transition: color 0.25s ease;
}
.block:hover,
.block:hover::before {
  color: red;
}
```
