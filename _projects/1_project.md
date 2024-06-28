---
layout: page
title: ReHEarSSE
description: Earbud-based Silent Speech Interface
img: assets/img/publication_preview/re_canal.jpg
importance: 1
category: work
related_publications: true
---


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/rehearsse teaser.jpg" title="ReHEarSSE Teaser" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (a) ReHEarSSE uses a novel earbud-based ultrasonic sensing method to infer silently spelled words, even if they are not in the training lexicon. (b) ReHEarSSE can be used while interacting with an extended-reality device for hands-free text input. (c) ReHEarSSE can also be used on-the-go while users’ hands are unavailable or inconvenient for text entry on a smartwatch or smart eyewear
</div>

Silent speech interaction (SSI) allows users to discreetly input text without using their hands. Existing wearable SSI systems typically require custom devices and are limited to a small lexicon, limiting their utility to a small set of command words. This work proposes ReHEarSSE, an earbud-based ultrasonic SSI system capable of generalizing to words that do not appear in its training dataset, providing support for nearly an entire dictionary’s worth of words{% cite rehearsse %}. As a user silently spells words, ReHEarSSE uses autoregressive features to identify subtle changes in ear canal shape. ReHEarSSE infers words using a deep learning model trained to optimize connectionist temporal classification (CTC) loss with an intermediate embedding that accounts for different letters and transitions between them. We find that ReHEarSSE recognizes unseen words with an accuracy of 89.3 ± 10.9%.
