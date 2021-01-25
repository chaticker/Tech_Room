### fain-in

```html
<div class="fade-in-box">
  This is fade-in-box
</div>
```

```css
.fade-in-box {
  display: inline-block;
  background: yellow;
  padding: 10px;
  animation: fadein 3s;
  -moz-animation: fadein 3s; /* Firefox */
  -webkit-animation: fadein 3s; /* Safari and Chrome */
  -o-animation: fadein 3s; /* Opera */
}
@keyframes fadein {
    from {
        opacity:0;
    }
    to {
        opacity:1;
    }
}
@-moz-keyframes fadein { /* Firefox */
    from {
        opacity:0;
    }
    to {
        opacity:1;
    }
}
@-webkit-keyframes fadein { /* Safari and Chrome */
    from {
        opacity:0;
    }
    to {
        opacity:1;
    }
}
@-o-keyframes fadein { /* Opera */
    from {
        opacity:0;
    }
    to {
        opacity: 1;
    }
}
```

### fain-out

```css
.fade-in-box {
  display: inline-block;
  background: yellow;
  padding: 10px;
  animation: fadeout 3s;
  -moz-animation: fadeout 3s; /* Firefox */
  -webkit-animation: fadeout 3s; /* Safari and Chrome */
  -o-animation: fadeout 3s; /* Opera */
}
@keyframes fadeout {
    from {
        opacity:1;
    }
    to {
        opacity:0;
    }
}
@-moz-keyframes fadeout { /* Firefox */
    from {
        opacity:1;
    }
    to {
        opacity:0;
    }
}
@-webkit-keyframes fadeout { /* Safari and Chrome */
    from {
        opacity:1;
    }
    to {
        opacity:0;
    }
}
@-o-keyframes fadeout { /* Opera */
    from {
        opacity:1;
    }
    to {
        opacity: 0;
    }
}
```
