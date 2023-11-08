### CSS Animation

Which of the following would create the below animation? Moving the mouse over the div should double its size, and the animation should happen over 500ms.

```html
<style>
  div {
    height: 50px;
    width: 50px;
    background: #3ba596;
    border-radius: 50%;
  }
</style>
<div class="greyBall"></div>
```

- [ ] .greyBall:hover { transform:scale(2); animate: 500ms; }
- [x] .greyBall:hover { transform:scale(2); transition: 500ms transform; }
- [x] .greyBall:hover { transform:scale(2); transition: 0.5s; }
- [ ] .greyBall:focus { transform:scale(2); animate: 0.5s; }
