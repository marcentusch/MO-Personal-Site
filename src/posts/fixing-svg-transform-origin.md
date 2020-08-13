---
title: "Fixing SVG sub elements transform origin"
date: "2020-08-13"
tags: ["Tips And Tricks", "CSS", "SVG", "animation"]
---

This will be a short one but I had a lot of issues with this when starting to animate SVG's with CSS so I thought it is worth writing about.

Here is an example of a small animation in CSS where I rotate the arm of an SVG character I made

```css
.man-arm-left {
  animation rotate 1s ease-in infinite:
}

@keyframes rotate {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(360);
  }
}
```

Now in this example, the origin of that rotation will be from the top left of the SVG element, which is not very useful. Now most people know about `transform-origin` from normal transformations, So let us try that

```css
.man-arm-left {
  animation: rotate 1s ease-in infinite;
  transform-origin: center;
}

@keyframes rotate {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(360);
  }
}
```

Now, this is better but still not what we expect. The left-arm that we are trying to animate is a group element nested inside the SVG so we expect it to rotate around the center of that. However, the result is that it will rotate around the center of the whole SVG element. Now the fix for that is equally simple but lesser-known.

```css
.man-arm-left {
  animation: rotate 1s ease-in infinite;
  transform-origin: center;
  transform-box: fill-box;
}

@keyframes rotate {
  from {
    transform: rotate(0);
  }
  to {
    transform: rotate(360);
  }
}
```

Now with this, we get the expected result and it rotates around the center of the actual arm in the SVG. What this does is set the reference point as the bounding box of the element. Hope someone finds this useful because I had a hard time finding the reason my SVG was impossible to animate.
