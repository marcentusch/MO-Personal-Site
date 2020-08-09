---
title: "Marc Obel's Blog"
layout: "layouts/feed.html"
pagination:
  data: collections.blog
  size: 5
permalink: "blog{% if pagination.pageNumber > 0 %}/page/{{ pagination.pageNumber }}{% endif %}/index.html"
paginationPrevText: "Newer posts"
paginationNextText: "Older posts"
paginationAnchor: "#post-list"
---

For now these posts are just lorem ipsum. I am working on adding some real content.
