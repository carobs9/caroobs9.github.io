---
layout: post
title: a post with images
date: 2024-05-15 21:01:00
description: this is what included images could look like
tags: formatting images
categories: sample-posts
thumbnail: assets/img/gmms1.png
---

This is an example post with image galleries.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gmms1.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A simple, elegant caption looks good between image rows, after each row, or doesn't have to be there at all.
</div>

The rest of the images in this post are all zoomable, arranged into different mini-galleries.
