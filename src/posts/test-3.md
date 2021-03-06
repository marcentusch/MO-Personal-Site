---
title: "How to make an animated gradient header"
date: "2020-08-10"
tags: ["Tips And Tricks", "CSS", "Animations", "Tutorial"]
---

I think this is a pretty cool effect and it can be as subtle or as crazy looking as you want.
The main trick here is that we use `background-clip` to clip the background around the text. When this is paired with a transparent text you can easily animate the background however you want to get the desired effect.

### Step 1: Gradient text

```css
h1 {
  -webkit-background-clip: text;
  color: transparent;
  display: inline-block;
  background-image: linear-gradient(-45deg, #b8c1ec, #fffffe, #eebbc3, #f9bc60);
}
```

The bit about background-clip and transparent text I explained above, however, we also need to set `inline-block` so our header only fills as much as the content within. Since our background is only visible where we have text, it does not make sense for it to fill out anything else.

Lastly, we create a gradient. I just grabbed some colors from [HappyHues](https://www.happyhues.co/) that looked nice.

### Step 2: Animating our gradient

```css
background-size: 400% 400%;
animation: gradient-scroll 12s ease infinite;

@keyframes gradient-scroll {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
```

We scale up our `background-size` so that the header only shows a smaller part of it. A nice way to think about it is that with this setup our header is the viewport through to the background and then when we animate the position of the background it will give the impression of an animated gradient.

Then we just add keyframes for moving the background around in both x and y and give the animation a long duration so it is a bit more subtle. This can easily be changed to a different effect by changing the easing, duration, and keyframes.

## Final result

<p class="codepen" data-height="241" data-theme-id="dark" data-default-tab="result" data-user="marcentusch" data-slug-hash="qBbwXEg" style="height: 241px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Animated gradient header">
  <span>See the Pen <a href="https://codepen.io/marcentusch/pen/qBbwXEg">
  Animated gradient header</a> by Marc Obel (<a href="https://codepen.io/marcentusch">@marcentusch</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>
