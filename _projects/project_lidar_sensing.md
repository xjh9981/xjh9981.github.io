---
layout: page
title: LiDAR Sensing
description: <h5>Smartphone LiDAR for Multi-Point Pulmonary Function Sensing</h5>
img: assets/img/publication_preview/banner_lisen.png
importance: 3
category: work
giscus_comments: false
related_publications: true
---

LiSen {% cite lisen %} is my internship project at Microsoft Research Asia (MSRA) Shanghai. It explores a simple question behind my SenSys 2026 presentation: can the LiDAR already built into commodity smartphones move wireless sensing from a single representative point to hundreds of spatially meaningful body points? We use this new multi-point sensing capability for contact-free pulmonary function sensing, recovering the full forced vital capacity (FVC) volume-time curve without requiring new-user calibration, bare-chest exposure, or special hardware beyond a LiDAR-equipped phone.

<p>
  <a class="btn btn-sm btn-outline-primary" href="{{ '/assets/pdf/Git_TAPS_Ver__Multi_Point_Sensing_LiSen_MSRA.pdf' | relative_url }}">Paper PDF</a>
  <a class="btn btn-sm btn-outline-secondary" href="https://doi.org/10.1145/3774906.3802752">DOI</a>
</p>

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/publication_preview/banner_lisen.png" title="LiSen teaser" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
  LiSen turns a smartphone LiDAR depth stream into dense torso measurements, then separates chest and abdominal motion to infer pulmonary volume curves.
</div>

<h3>
  <div style="display: flex; align-items: center;">
    <span style="white-space: nowrap;">Why LiDAR?</span>
    <div style="flex-grow: 1; height: 1px; background-color: black; margin-left: 10px;"></div>
  </div>
</h3>

Conventional RF and acoustic sensing systems often observe a target as one blended reflection path. That is enough for coarse respiration-rate monitoring, but it is not enough for pulmonary function testing, where chest and abdomen movements carry different information about the true air volume. Smartphone LiDAR projects hundreds of narrow infrared beams and provides a dense depth map, making it possible to observe a moving torso as a surface rather than as a single point.

For the conference talk, the most important message is that multi-point sensing is not just "more data." It gives the system the spatial references needed to cancel body motion, separate torso regions, and reason about local geometric deformation.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    <h4>Body Motion</h4>
    Forced breathing often comes with large involuntary torso movement, such as leaning forward. LiSen uses relatively stable shoulder and pelvis landmarks as references, fits the torso motion, and subtracts this non-respiratory component from the depth field.
  </div>
  <div class="col-sm mt-3 mt-md-0">
    <h4>Pressure Difference</h4>
    The physical volume change of the torso is not identical to the air volume reported by spirometry, because intrapulmonary pressure changes during forceful exhalation and inhalation. LiSen uses local geometric coherence and a physics-informed neural model to compensate for this hidden factor.
  </div>
  <div class="col-sm mt-3 mt-md-0">
    <h4>Chest vs. Abdomen</h4>
    People rely on different mixtures of chest and abdominal breathing. LiSen segments these regions by exploiting their different displacement patterns, then models them as parallel inputs rather than collapsing them into one signal.
  </div>
</div>

<h3>
  <div style="display: flex; align-items: center;">
    <span style="white-space: nowrap;">System Pipeline</span>
    <div style="flex-grow: 1; height: 1px; background-color: black; margin-left: 10px;"></div>
  </div>
</h3>

LiSen processes synchronized RGB and LiDAR depth streams from ARKit. The system first extracts a person-centered LiDAR region of interest, converts the depth map into a 4D point-cloud sequence, and then estimates the FVC volume-time curve through three multi-point modules:

1. **Multi-Point Reference (MPRef):** tracks shoulder and pelvis landmarks to estimate and remove global torso motion.
2. **Chest-Abdomen Segmentation (CASeg):** divides the motion-free torso surface into chest and abdomen regions using depth-displacement patterns.
3. **Local Coherence Extraction (PINN):** encodes multi-scale point-cloud patches, combines local deformation with basic metadata, and predicts respiratory volume while accounting for pressure-volume behavior.

During data collection, the examinee sits near the phone, raises both arms to avoid occluding the torso, and performs standard FVC maneuvers with a spirometer used as ground truth. The prototype was implemented on iPhone 12 Pro, iPhone 13 Pro, and iPad Pro M1 devices.

<h3>
  <div style="display: flex; align-items: center;">
    <span style="white-space: nowrap;">Evaluation Snapshot</span>
    <div style="flex-grow: 1; height: 1px; background-color: black; margin-left: 10px;"></div>
  </div>
</h3>

<div class="table-responsive">
  <table class="table table-sm">
    <thead>
      <tr>
        <th>Question</th>
        <th>Paper result</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Who participated?</td>
        <td>35 examinees from 3 countries, ages 21-65, with FVC ranging from 3.01 L to 6.88 L.</td>
      </tr>
      <tr>
        <td>How accurate is the volume curve?</td>
        <td>0.24 L mean absolute error for forced expiration and 0.30 L for subsequent forced inspiration.</td>
      </tr>
      <tr>
        <td>How accurate are common PFT indices?</td>
        <td>Mean errors of 7.10% for FVC, 9.82% for FEV1, 7.84% for FEV1/FVC, and 10.05% for FIVC.</td>
      </tr>
      <tr>
        <td>Does it generalize beyond one setup?</td>
        <td>Across 15 perturbed conditions, expiration MAE stayed below 0.42 L and inspiration MAE below 0.48 L.</td>
      </tr>
      <tr>
        <td>How much device resource is needed?</td>
        <td>A standard three-trial spirometry protocol is estimated to consume about 2.1%-3.0% battery, with temporary LiDAR cache files deleted after analysis.</td>
      </tr>
    </tbody>
  </table>
</div>

<h3>
  <div style="display: flex; align-items: center;">
    <span style="white-space: nowrap;">Takeaways</span>
    <div style="flex-grow: 1; height: 1px; background-color: black; margin-left: 10px;"></div>
  </div>
</h3>

- **From one point to hundreds:** LiSen reframes smartphone LiDAR as a practical multi-point wireless sensing modality, not only as a 3D scanning or AR component.
- **Pulmonary function without custom hardware:** The system estimates full FVC curves and derived indices using commodity LiDAR-equipped phones, with a medical spirometer used only for ground-truth collection.
- **Spatial structure solves practical sensing problems:** The added spatial context enables motion cancellation, chest-abdomen separation, and pressure-aware volume estimation.
- **Best suited for short, close-range tests:** LiDAR is attractive for user-initiated at-home PFT-style measurements, while its range, field of view, and power profile make it less suitable for always-on long-term respiration monitoring.

LiSen is intended as a research prototype toward accessible pulmonary screening and home-care monitoring. It does not replace clinical spirometry, but it shows that everyday LiDAR-equipped devices can support a much richer class of contact-free health sensing than single-point respiration monitoring.
