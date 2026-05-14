---
layout: page
title: ElectroTwin
description: Digital Twin-Driven Design and Scheduling Framework for Electroplating Facilities
img: assets/img/1.jpg
importance: 2
category: research
---

<div><h3><b>Overview</b></h3></div>

`ElectroTwin` is a digital twin-driven decision-support framework designed to optimize the design and scheduling of real-world electroplating facilities. The project addresses the `Cyclic Hoist Design and Scheduling Problem (CHDSP)`, where facility operators must determine the appropriate number of hoists and feasible movement schedules while satisfying strict soaking-time and cycle-time constraints.

In electroplating lines, delayed or inefficient hoist movement can cause parts to remain in chemical tanks longer than allowed, increasing the risk of corrosion, quality degradation, and environmental pollution. However, in many real-world facilities, these scheduling decisions are still handled manually or outsourced due to the complexity of mathematical optimization. This project aimed to make the decision-making process faster, more transparent, and easier for non-expert operators to use.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/electrotwin_outline.png" title="Outline for Electrotwin" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>Problem</b></h3></div>

Electroplating facilities require precise coordination between multiple tanks, stages, parts, and hoists. The main challenge is to determine:
 - The minimum or appropriate number of hoists required
 - Feasible hoist movement schedules
 - Handover stages between hoists
 - Schedules that satisfy soaking-time and cycle-time constraints
 - Operational configurations that reduce cost while maintaining production quality

<hr style="border: 1px solid #ccc;">

<div><h3><b>Proposed Solution</b></h3></div>

I contributed to the development of `ElectroTwin`, a decision-support system that combines facility data, scheduling logic, and visual analytics into an interactive digital twin framework.

The core component of the system is `C-Search`, a constraint-based search algorithm designed to identify the appropriate number of hoists and their feasible movements within a given cycle time. Instead of requiring operators to manually formulate a new optimization model for each facility configuration, ElectroTwin dynamically injects operational constraints and system states into the search process. This allows the framework to solve diverse electroplating scheduling problems without manual reformulation.

Key features include:
 - Built a digital representation of real-world electroplating facilities
 - Developed a **constraint-based search approach** for hoist design and scheduling
 - Automated the process of **determining hoist count, handover stages, and movement schedules**
 - Integrated **visual analytics for schedule interpretation and decision support**
 - Supported **what-if analysis** for different tank and hoist configurations
 - Designed the framework to be usable by non-expert facility operators

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/electrotwin_failcase.png" title="" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/electrotwin_csearch.png" title="" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>System Implementation</b></h3></div>

ElectroTwin was implemented as a graphical user interface application using `Python, Tkinter, and Matplotlib`. The system allows users to load electroplating facility data, input cycle-time constraints, run the C-Search algorithm, and visually analyze the resulting schedules.

The application includes several user-facing functions:
 - `(a) Data Load Function:` Constructs the digital twin using facility information such as tank types, soaking times, number of tanks, and hoist specifications.
 - `(b) Cycle Time Input and Execution Function:` Runs C-Search to determine the appropriate number of hoists and feasible movements.
 - `(c) Output Function:` Displays the resulting hoist count, handover points, and tank utilization.
 - `(d) Operation Visualization Function:` Simulates part movement and hoist operation across the electroplating line.
 - `(e) Visual Analytics Function:` Provides Gantt chart analysis, bottleneck analysis, and cost-profit analysis.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/electrotwin_gui.png" title="Outline for Electrotwin" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


<hr style="border: 1px solid #ccc;">

<div><h3><b>Visual Analytics and Decision Support</b></h3></div>

A major goal of this project was not only to generate feasible schedules, but also to make the results interpretable for facility operators. ElectroTwin provides multiple visual analytics tools to support operational decision-making.

The `Gantt chart analysis` visualizes hoist movements, soaking periods, and handover stages. This helps operators understand whether parts are transported on time and how hoists are coordinated throughout the production cycle.

The `bottleneck analysis` identifies tanks or stages with high cumulative processing time. In the industrial case studies, bottlenecks were often observed around stages with multiple tanks, which are typically installed to balance throughput.

The `cost-profit analysis` evaluates how changes in the number of tanks and hoists affect cycle time, annual cost, annual profit, and overall financial feasibility. This allows operators to compare alternative facility configurations before making investment decisions.

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/electrotwin_gantt.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/electrotwin_bottleneck.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/electrotwin_cost.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>Industrial Case Studies</b></h3></div>

**The framework was evaluated using three real-world industrial electroplating cases from South Korea.** These cases included different numbers of stages, tanks, soaking times, and cycle-time requirements. The experiments demonstrated that ElectroTwin can scale across different facility configurations and generate practical scheduling solutions.

Compared with the conventional outsourcing-based method, C-Search achieved significantly faster computation while reducing operational cost in larger cases:

 - **Case 1:** Same objective value as the conventional method, but reduced computation time from 24 hours to 48.51 seconds.
 - **Case 2:** Reduced required hoists from 6 to 5 and improved the objective value from 315,600 to 285,600.
 - **Case 3:** Reduced required hoists from 6 to 4 and improved the objective value from 306,600 to 246,600.

Across all cases, ElectroTwin generated solutions in `less than two minutes`, while the conventional method required approximately 24 hours.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/electrotwin_results.png" title="Outline for Electrotwin" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<hr style="border: 1px solid #ccc;">

<div><h3><b>Impact</b></h3></div>

This project demonstrates how digital twin technology, optimization algorithms, and visual analytics can be combined to support real-world manufacturing decision-making.

From an operational perspective, ElectroTwin helps facility operators reduce dependency on outsourcing companies, shorten scheduling decision time, and evaluate investment alternatives more transparently. From a sustainability perspective, better hoist scheduling can reduce the risk of excessive soaking, corrosion, and process inefficiency. From a managerial perspective, the system enables data-driven what-if analysis by simulating how different numbers of tanks and hoists affect performance and financial outcomes.

<hr style="border: 1px solid #ccc;">

<div><h3><b>Key Contributions</b></h3></div>

 - Developed a digital twin-driven decision-support framework for electroplating facility design and scheduling
 - Designed and implemented C-Search, a constraint-based search algorithm for determining hoist count and movement schedules
 - Built a GUI-based prototype using Python, Tkinter, and Matplotlib
 - Integrated Gantt chart, bottleneck, and cost-profit visual analytics
 - Validated the framework using three real-world industrial case studies
 - Demonstrated faster computation and lower operational costs compared with a conventional outsourcing-based approach

<!-- {% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %} -->
