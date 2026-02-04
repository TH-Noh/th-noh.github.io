---
layout: page
title: Data Analytics Competition
description: University of Utah - 2024 Gamday Analtycis Challenge
img: assets/img/gameday.jpg
importance: 2
category: competition
related_publications: false
---

<div><h3><b>Overview</b></h3></div>
This project was conducted as part of the Game Day Analytics Challenge, where I analyzed real-world Twitter data to evaluate the effectiveness of Super Bowl advertisements from multiple perspectives. The experience was particularly meaningful as it involved large-scale, time-sensitive social media data and required translating analytical results into actionable insights.

<!-- To give your project a background in the portfolio page, just add the img tag to the front matter like so:
    ---
    layout: page
    title: project
    description: a project with a background image
    img: /assets/img/12.jpg
    --- -->
<hr style="border: 1px solid #ccc;">

<div><h3><b>Time-Based Analysis</b></h3></div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/gdac_time_series.jpg" title="time-based analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

To understand how audience reactions evolved during the Super Bowl, I first analyzed tweet volumes over time.
By aligning tweet timestamps with the game timeline, I identified how brand-related discussions surged immediately after advertisements were aired, revealing both short-term spikes and sustained engagement patterns across different brands.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Cost Analysis & Sentiment Analysis</b></h3></div>

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/gdac_cost.jpg" title="cost analysis" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/gdac_sentiment.jpg" title="sentiment analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

To assess advertising effectiveness beyond simple engagement volume, I conducted additional analyses from multiple viewpoints:

- **Cost Analysis:** Estimated advertising cost per tweet by combining Super Bowl ad pricing with tweet volume, enabling efficiency comparisons across brands.

- **Sentiment Analysis:** Applied sentiment analysis to distinguish positive and negative audience reactions, highlighting that high engagement does not always imply positive brand perception.

These analyses demonstrated that advertising effectiveness cannot be evaluated using a single metric alone.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Social Network Analysis & Visualization</b></h3></div>
<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/gdac_network1.jpg" title="cost analysis" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/gdac_network2.jpg" title="sentiment analysis" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/gdac_network3.jpg" title="sentiment analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The images show network graphs at three different stages of the game, from left to right: at the start of the game, midway through the game, and at the end of the game.
</div>

To further explore audience behavior, I modeled the data as a network:

- **Nodes:** Social media posts and advertising companies

- **Edges:** User reactions and interactions related to advertisements

This network visualization revealed how audience attention expanded and evolved as the Super Bowl progressed, allowing intuitive observation of which companies gained momentum and influence throughout the event.