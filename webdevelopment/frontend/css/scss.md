# SCSS

"Sass is the most mature, stable, and powerful professional grade CSS extension language in the world", [Sass](https://sass-lang.com/).

Basically it reduces a lot of the complexity of maintaining large applications with a lot of CSS.

## Tips:

- &:

"A nested & selects the parent element in both SASS and LESS. It's not just for pseudo elements, it can be used with any kind of selector", [anthonygore](https://stackoverflow.com/questions/13608855/what-does-an-before-a-pseudo-element-in-css-mean).

```css
h1 {
    &.class {

    }
}

/* translates to: */

h1.class {

}
```