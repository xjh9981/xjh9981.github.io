---
layout: page
title: Earable SSI
description: <h5> Earable-based Silent Speech Interface </h5>
img: assets/img/publication_preview/re_canal.png
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

Silent speech interaction (SSI) allows users to discreetly input text without using their hands. Existing wearable SSI systems typically require custom devices and are limited to a small lexicon, limiting their utility to a small set of command words. This work proposes ReHEarSSE, an earbud-based ultrasonic SSI system capable of generalizing to words that do not appear in its training dataset, providing support for nearly an entire dictionary’s worth of words {% cite rehearsse %}. As a user silently spells words, ReHEarSSE uses autoregressive features to identify subtle changes in ear canal shape. ReHEarSSE infers words using a deep learning model trained to optimize connectionist temporal classification (CTC) loss with an intermediate embedding that accounts for different letters and transitions between them. We find that ReHEarSSE recognizes unseen words with an accuracy of 89.3 ± 10.9%.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/hearid_banner.png" title="HEarID Teaser" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (ab) potential threats against SSI usage; (c) HEar-ID uses multi-task learning (MTL) to authenticate user identity and reliably infer silent speech; 
</div>

While users tend to prefer SSI over traditional speech recognition in public contexts, prior SSI-related works hardly consider the safety issues. While normal voice-based authentication mitigates these risks by verifying
the speaker’s identity before granting access, it can be vulnerable to
replay and injection attacks (e.g., triggering Siri via a loudspeaker),
leaving an imperative need for developing a reliable SSI system.
We analyzed and found that the silent speech recognition task
and the speaker authentication task are correlated rather than
independent. The inherent structure uniqueness of each individual’s ear canal creates distinct acoustic propagation paths, so that
subtle ear canal deformations encode both the utterance content
and speaker identity. 

In this work, we enable reliable SSI by proposing HEar-ID, which
only leverages a commodity active noise-canceling earbud to emit
an inaudible OFDM signal and record both ultrasonic reflections
and whisper audio to enable silent spelling input (e.g. /i: eI Ar/
for the word "ear") and user verification with a single machine
learning model. 
In the preliminary experiments, HEar-ID consistently delivered
promising results: for 11 participants, the system reliably rejected
impostors with a false positive rate (FPR) of 3.2% and a true positive
rate (TPR), accompanying 90.25% Top-1 word recognition accuracy
for eight of them.