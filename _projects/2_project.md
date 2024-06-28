---
layout: page
title: Micro-Mobility Safety
description: <div style="text-align: center;">[ Advanced Cyclist-Assistance Schemes ] </div>
img: assets/img/bicycle_cover.jpg
importance: 2
category: work
giscus_comments: true
---

Cycling must be safe, and perceived as such, if micro-mobility trips by all populations are to increase, and the benefits in traffic
decongestion and carbon emission cut are to be realized. WHO estimates that 40,000 cyclists died in road accident in 2016. There
is an urgent need to address this problem by low-cost and robust safeguard systems.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/bicycle project.png" title="teaser" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    We developed riding safegard with regard to two categories: (a) Distracted behavior recognition (b) Riding Maneuver Prediction. 
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <h3>  
        <div style="display: flex; align-items: center;">
        <span style="white-space: nowrap;"> HEADSENSE </span>
        <div style="flex-grow: 1; height: 1px; background-color: black; margin-left: 10px;"></div>
        </div> </h3>
        We present HeadSense {% cite headsense %}, a helmet-based system that leverages the inertial motion unit (IMU) to recognize 4 distracted behaviors: checking handlebar-mounted devices, using smartphones, attracting to the roadside element, and abreast riding. 
        
        The feasibility lies as followed:
        
        - The head dynamic is a strong indicator of the rider's eyesight / attention. And the helmet, as an essential bicycle accessory, follows the same movement pattern as rider's head.
        
        - The rider’s head shows unique motion patterns during distracted riding behaviors. These patterns consist of a series of abnormal head movements.
        
        Evaluation results show HeadSense can segment visual search into episodes with an accuracy of up to 86.14%. Additionally, from sequences of episodes, it can effectively detect distracted riding behaviors at an average precision of 85.04%. 
    </div>   
    <div class="col-sm mt-3 mt-md-0">
        <h3><div style="display: flex; align-items: center;"> <span style="white-space: nowrap;"> 
        HEADMON 
        </span> <div style="flex-grow: 1; height: 1px; background-color: black; margin-left: 10px;"></div>
        </div> </h3>
        Detection of ongoing maneuver may be less effective in accident prevention. In this work {% cite headmon %} {% cite rideguard %}, we take a step further to explore the feasibility of using riders’ head dynamics or handlebar motion to predict their riding maneuvers with two key observations:
        Rider needs to observe the traffic situation in advance based on their riding maneuver intentions.
        For different maneuver intentions, the rider's head dynamics (such as turning left and right) are also different. 
        
        We constructed an Attention-based network to solve the prediction problem. The precision of riding maneuver prediction is at least 0.80 under 4 seconds time gap. We also finds that the accuracy would be improved with longer detection window size.
        The results indicate a novel start on improving micro-mobility safety.
    </div>
    <div class="col-sm mt-3 mt-md-0">
                <h3><div style="display: flex; align-items: center;"> <span style="white-space: nowrap;"> 
        DOUBLECHECK 
        </span> <div style="flex-grow: 1; height: 1px; background-color: black; margin-left: 10px;"></div>
        </div> </h3>
        DoubleCheck is a method that utilizes a handlebar-mounted smartphone to detect single-handed cycling and followed distracting secondary tasks. The work was established on the premise that single-handed cycling undermines the stability of handlebar during cycling. Preliminary data shows that For both acceleration and angular speed:
        
        - The signal has denser power over the frequency band during single-handed cycling.
        
        - The signals contain periodic components
        
        Accordingly, we adopt Autoregressive Model, featuring robust performance in extracting features of periodic time-series signal. 
        Experiment with 22 participants on asphalt and pavement demonstrated that DoubleCheck achieves an F1-score of 0.96 for hand detection and 0.69 for distraction recognition.
    </div>
</div>