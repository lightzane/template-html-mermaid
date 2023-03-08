# Template HTML Mermaid

Just a static `HTML` using https://mermaid.js.org/ with https://d3js.org/ to pan and zoom

## Initialize Mermaid

**CDN**

```html
<script src="https://unpkg.com/mermaid@9.4.0/dist/mermaid.min.js"></script>
```

Then add this `<script>` inside the `<body>` of your **HTML** page

```js
mermaid.initialize({
  showSequenceNumbers: true,
  themeVariables: {
    fontFamily: '-apple-system, Segoe UI, Roboto, Arial',
  },
});
```

## Pan and Zoom

This will enable `pan and zoom` to your diagram when it becomes huge for the view

**CDN**

```html
<script src="https://d3js.org/d3.v7.min.js"></script>
```

Then add this `<script>` inside the `<body>` of your **HTML** page

```js
window.addEventListener('load', () => {
  var svgs = d3.selectAll('.mermaid svg');
  svgs.each(function () {
    var svg = d3.select(this);
    svg.html('<g>' + svg.html() + '</g>');
    var inner = svg.select('g');
    var zoom = d3.zoom().on('zoom', (event) => {
      inner.attr('transform', event.transform);
    });
    svg.call(zoom);
  });
});
```
