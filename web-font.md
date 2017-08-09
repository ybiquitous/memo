# Web Font

- https://github.com/typekit/webfontloader
- https://blog.aroundit.net/webfont-fout/
- https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/webfont-optimization
- https://www.lockedowndesign.com/load-google-fonts-asynchronously-for-page-speed/
- https://fonts.google.com/specimen/Droid+Serif?selection.family=Droid+Serif:400,700

```js
WebFontConfig = {
  google: {
    families: [
      // 'Droid Serif:400,700',
      // 'Open Sans:400,700',
      'Fjalla One:400,700'
    ]
  }
};

(function(d) {
  var wf = d.createElement('script'), s = d.scripts[0];
  wf.src = 'https://ajax.googleapis.com/ajax/libs/webfont/1.6.26/webfont.js';
  wf.async = true;
  s.parentNode.insertBefore(wf, s);
})(document);
```

- https://blog.graphiq.com/finding-the-best-free-fonts-for-numbers-25c54002a895

```js
const style = document.createElement('style');
document.head.appendChild(style);
const styleSheet = style.sheet;
const fontFamily = 'Fjalla One'; // 'Droid Serif' 'Open Sans'
[
  `.month-price-value { font-family: "${fontFamily}"; font-size: 2.4rem; }`,
  '.month-price-value::before { content: "¥"; }'
].forEach(rule => styleSheet.insertRule(rule, styleSheet.cssRules.length));
```
