---
layout: page
title: Centrifugal Clutch Optimization
description: MAE 413 (Design of Mechanical Systems) final project.
img: assets/img/clutch/clutch_thumb_1.png
importance: 3
category: school

_styles: >
  .fake-img {
    background: #bbb;
    border: 1px solid rgba(0, 0, 0, 0.1);
    box-shadow: 0 0px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 12px;
  }
  .fake-img p {
    font-family: monospace;
    color: white;
    text-align: left;
    margin: 12px 0;
    text-align: center;
    font-size: 16px;
  }
  .fixed-height-row img {
    width: 100% !important;
    height: 325px !important;
    object-fit: contain !important;
  }
---

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/clutch/clutch_CAD.png" class="rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Figure 1: (RIGHT) Schematic of patent centrifugal clutch design, and (RIGHT) parameterized CAD model of clutch design created from overall diameter provided in patent and overlaying the schematic in a SolidWorks sketch.
</div>

## The Project

This was my team's final project for the Design of Mechanical Systems class at NC State University (NCSU) taught by Dr. Eischen. The class is an overview of the theory behind mechanical elements--bolts, welds, gears, belt drives, etc.--paired with 3 team design projects that apply the theory learned.

The final project was as follows:

> 
Determine the principal dimensions (primarily the shoes and springs) of a centrifugal
clutch of the type described in US Patent 5,560, 465. The clutch is to be placed
between a load and a 5-hp 1750-rpm induction motor, to give initial engagement when
the motor speed is 1200 rpm and complete engagement (no further slipping) at 1450 rpm
and a torque of 225lb-.in. The clutch should be as compact as possible.
>
The referenced patent can be viewed [here](/assets/pdf/US5560465.pdf). 

## Centrifugal Clutches

Centrifugal clutches are often found in equipment or machinery in which it is desirable to only transmit rotational power to a given load above a certain operating RPM. Some classic examples are chainsaws, go-carts, or small motorized scooters. 

A typical example of a centrifugal clutch is shown in Figure 2. The main components are the drum (which is not shown in Figure 2, but would surround the assembly shown), shoes and associated springs, and the input shaft. When the RPM of the input shaft is high enough, the centrifugal force acting on the shoes overcomes the spring forces holding them to the input shaft, throwing them away from the center of the clutch until they contact the inside of the drum. The friction between the two surfaces then transmit the power of the input shaft to the drum / load. The shoes are kinematically restricted by pivot points, and by shoe springs with a spring rate chosen based on the desired engagement RPM.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/clutch/centrifugal_clutch.webp" class="rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Figure 2: Typical centrifugal clutch design. [1].
</div>

## High and Low Gain Clutch

The clutch presented in the patent is proposed to solve a few shortcomings of prior designs, including failure of the shoe springs due to the high stress within the hooks connecting them to the shoes, and catastrophic failure if the drum breaks, which would fling the shoes outward. These concerns are mainly addressed by the interlocking design of the shoes--the shoe springs (highlighted green in Figure 3) used are flat and ground compression springs rather than tension springs with hooks, and if the drum fails, the shoes are held together by the interlocked members (highlighted red).

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/clutch/clutch_annotated.png" class="rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Figure 3: Annotated High and Low Gain Clutch Design [2].
</div>

However, the main concern the patent addresses is that prior designs do not have a smooth transition during initial engagement of the shoes. This is solved by the wedge members and associated compression springs (highlighted orange) that split the operation of the clutch into **Low Gain / Threshold Gain** mode and a **High Gain** mode:

- In the *low-gain* region, the shoes have have been thrown outward to begin making contact with the drum, but the wedge members are held against the *dogs* (highlighted blue) of the input shaft by the wedge springs. The operating RPM of this region starts at $\bf{S_o}$.

- As RPM increases, the *threshold gain* region beings as the wedge members being to move radially outward, compressing the wedge springs. This region begins at RPM $\bf{S_1}$.

- During both the low-gain and threshold-gain modes, the shoes are engaged to the inside of the drum, *but slip has not been eliminated*. 

- If the RPM continues to increase, the clutch enters the *high-gain* region as the wedges fully contact the end of their drive slots. The RPM this transition occurs is $\bf{S_2}$. 

High and low-gain curves provided in the patent's analysis can be seen in Figure 4. In actual operation during threshold-gain mode, the torque transmitted would transition from the low-gain to the high-gain curve, with full engagement occuring at the intersection of the high-gain curve with the vertical dotted line represent $S_2$.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/clutch/patent_graph.png" class="rounded z-depth-1" %}
        <div class="caption">
        Figure 4: Plot of low ($T_{CL}$) and high-gain ($T_{CH}$) curves from the design analyzed within the patent. $T_E$ is the "available or average torque" for the motor used for the patent author's analysis in order to linearize the low-gain curve. The vertical dotted lines represent different values of $S_2$, depending on the choice of wedge springs [2].
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/clutch/clutch_force_lg.png" class="rounded z-depth-1" %}
        <div class="caption">
        Figure 5: Diagram of the forces associated with low gain mode (when the shoes have engaged with the inner drum, but the wedge members / springs haven't yet fully compressed) [2].
        </div>
    </div>
</div>
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
            {% include figure.liquid loading="eager" path="assets/img/clutch/clutch_force_hg.png" class="rounded z-depth-1" %}
            <div class="caption">
            Figure 6: Diagram of the forces associated with high gain mode (once the wedge member contacts the end of the drive slot) [2].
            </div>
        </div>
</div>

In other words, the centrifugal force on the wedge members at $\bf{S_2}$ is equal to the compressive force on the wedge springs. Once this occurs, the radial contribution of the normal force $F_N$ between the wedge and the associated dog of the input shaft, $F_{Y2}$, begins contributing to the total outward force acting on the shoe. A diagram for low-gain forces associated with the wedge can be seen in Figure 5, and can be compared with the high-gain forces seen in Figure 6. 

## Governing Equations



## Optimization

For optimization, we focused treating the overall diameter and width of the drum as our primary parameters, and derived all other geometry from a parameterized CAD model. Detailed dimensions were not given in the patent other than overall diameter of the drum, so the closest way to derive the other geometry was to overlay the schematic, which was assumed to be drawn to scale, over a the sketch plane within SolidWorks. This model was shown at the top of page in Figure 1, and a portion of the data sheet is shown below.

$$
\begin{array}{c|c|c|c|c|c}
\hline
\text{Radius of Drum (in)} & \text{Radius of Gyration (in)} & \text{Wedge Radius of Gyration (in)} & \text{Volume Shoe (in}^3\text{)} & \text{Volume of Wedge (in}^3\text{)} & \text{Other Geometry} \\
6.00 & 1.86 & 1.80 & 5.684 & 0.64697 & \dots \\
5.75 & 1.78 & 1.73 & 4.96639 & 0.5463 & \dots \\
5.50 & 1.70 & 1.66 & 4.25946 & 0.4781 & \dots \\
5.25 & 1.63 & 1.58 & 3.65316 & 0.4158 & \dots \\
5.00 & 1.55 & 1.50 & 3.25000 & 0.35379 & \dots \\
\dots & \dots & \dots & \dots & \dots & \dots
\end{array}
$$


<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/clutch/design_plot_rad.png" class="rounded z-depth-1" %}
        <div class="caption">
        Figure 7:
        </div>
    </div>
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/clutch/design_plot_width.png" class="rounded z-depth-1" %}
        <div class="caption">
        Figure 8: 
        </div>
    </div>
</div>
