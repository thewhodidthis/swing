## about

Helps create harmonograph style patterns.

## setup

Load via script tag:

```html
<!-- Just an IIFE namespaced `swing` -->
<script src="https://thewhodidthis.github.io/swing/swing.js"></script>
```

Source from an import map:

```json
{
  "imports": {
    "@thewhodidthis/swing": "https://thewhodidthis.github.io/swing/main.js"
  }
}
```

Download from GitHub directly, using _npm_ for example:

```sh
# Add to package.json
npm install thewhodidthis/swing
```

## usage

Pass in minimum amplitude and frequency arguments and call the resulting function over time. For example,

```js
import swing from "@thewhodidthis/swing"

// Lissajous curve wrapper (no damping).
const driver = (A = 1, B = A, a = 1, b = a * 2, phase = Math.PI * 0.5) => {
  const x = swing(A, a, phase)
  const y = swing(B, b, phase)

  return t => ({ x: x(t), y: y(t) })
}

// Points for the Lemniscate of Gerono.
const lookup = driver(175, 100)

setInterval(() => {
  const t = Date.now()
  const { x, y } = lookup(t)

  console.log(x, y)
}, 1000)
```

## see also

- [Harmonography](https://thewhodidthis.com/harmonography/)
