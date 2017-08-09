## Web Font Loader

- https://github.com/typekit/webfontloader
- https://blog.aroundit.net/webfont-fout/
- https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/webfont-optimization
- https://www.lockedowndesign.com/load-google-fonts-asynchronously-for-page-speed/
- https://fonts.google.com/specimen/Droid+Serif?selection.family=Droid+Serif:400,700

```js
WebFontConfig = {
  google: {
    families: ['Droid Serif:400,700']
  }
};

(function(d) {
  var wf = d.createElement('script'), s = d.scripts[0];
  wf.src = 'https://ajax.googleapis.com/ajax/libs/webfont/1.6.26/webfont.js';
  wf.async = true;
  s.parentNode.insertBefore(wf, s);
})(document);
```
