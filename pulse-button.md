# Pulse button

https://www.google.co.jp/search?q=pulse+button+css

```html
<a href="#" class="pulse-button">詳細をチェック</a>
```

```css
.pulse-button {
  box-shadow: 0 0 0 0 rgba(232, 76, 61, 0.7);
  border-radius: 4px;
  background-color: red;
  color: white;
  padding: 5px;
  cursor: pointer;
  animation: pulse 1.25s infinite cubic-bezier(0.66, 0, 0, 1);
}

.pulse-button:hover {
  animation: none;
}

@keyframes pulse {
  to {
    box-shadow: 0 0 0 45px rgba(232, 76, 61, 0);
  }
}
```
