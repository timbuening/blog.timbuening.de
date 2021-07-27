---
title: Blog
body_classes: 'title-center title-h1h2'
visible: true
published: true
routable: true
content:
    items: '@self.children'
    order:
        by: date
        dir: desc
    limit: 10
    pagination: true
child_type: post
twig_first: false
---

