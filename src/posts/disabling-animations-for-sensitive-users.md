---
title: "Disabling animations for sensitive users"
date: "2020-08-11"
tags: ["Tips And Tricks", "Tutorial", "Accesibility"]
---

Some users may experience dizziness, nausea, headaches or other symptons when being exposed to the large amounts of movement on the screen of a lot of modern websites. Luckily with the support from all major browsers(not IE11) of `prefers-reduced-motion` we can easily accomodate these users with a single media query.

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01s !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01s !important;
    scroll-behavior: auto !important;
  }
}
```

This can be set in your global stylesheet and will work on all animations and transitions on your site. You can easily test this yourself on MacOS by going to _System Preferences --> Accessibility --> Display_ and checking the _Reduce motion_ checkbox.
