# custom-property-empty-lines-before

Require or disallow an empty line before custom properties.

```css
a {
  top: 10px;
                          /* ← */
  --custom-prop2: value;  /* ↑ */   
}                         /* ↑ */
/**                          ↑
 *                   This line */
```

## Options

### `always`

The following patterns are considered warnings:

```css
a {
  top: 10px;
  --custom-prop: value;
  --custom-prop2: value;
}
```

The following patterns are *not* considered warnings:

```css
a {
  top: 10px;

  --custom-prop: value;

  --custom-prop2: value;
}
```

### `never`

The following patterns are considered warnings:

```css
a {
  top: 10px;

  --custom-prop: value;

  --custom-prop2: value;
}
```

```css
a {

  --custom-prop: value;
  --custom-prop2: value;
}
```

The following patterns are *not* considered warnings:

```css
a {
  top: 10px;
  --custom-prop: value;
  --custom-prop2: value;
}
```

## Optional options

### `except: ["first-nested", "after-comment", "after-custom-property"]`

### `first-nested`

Reverse the primary option for custom properties that are nested and the first child of their parent node.

For example, with `"always"`:

The following patterns are considered warnings:

```css
.foo {

  --custom-prop: value;

  --custom-prop2: value;
}
```

The following patterns are *not* considered warnings:

```css
.foo {
  --custom-prop: value;

  --custom-prop2: value;
}
```
### `after-comment`

Reverse the primary option for custom properties that come after a comment.

For example, with `"always"`:

The following patterns are considered warnings:

```css
.foo {

  --custom-prop: value;
  /* comment */

  --custom-prop2: value;
}
```

The following patterns are *not* considered warnings:

```css
.foo {
  
  --custom-prop: value;
  /* comment */
  --custom-prop2: value;
}

```
### `after-custom-property`

Reverse the primary option for custom properties that come after another custom property.

For example, with `"always"`:

The following patterns are considered warnings:

```css
.foo {

  --custom-prop: value;

  --custom-prop2: value;
}
```

The following patterns are *not* considered warnings:

```css
.foo {

  --custom-prop: value;
  --custom-prop2: value;
}
```