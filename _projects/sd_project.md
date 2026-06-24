---
layout: page
title: Pick and Place Machine for Plant Matter
description: 2025-2026 Senior Design project for industry sponsor, Syngenta.
img: assets/img/papmfpm/SD_MACHINE.png
importance: 1
category: work
related_publications: 

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
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/SD_MACHINE.png" class="rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/winners.jpg" class="rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (LEFT) Final prototype machine delivered to sponsor. (RIGHT) Winners! From left to right, Myself, Simon Gneuss, Marissa Maynard, and Garett Fox. Last member not shown is Sherif Tawouss.
</div>

## The Problem

During my last semester at NC State University, I was lucky to get a very challenging but fun project for Senior Design. My team ended up winning 1st place out of the 6 teams that built prototypes. This post is a quick overview of the project. 

The sponsor was a research division within a larger Agricultural Technology company, Syngenta. As part of their work, the researchers grow pieces of plant matter within petri dishes called **callus** for selective breeding. These callus start off as just a few cells, but slowly grow over the course of weeks into small, irregular masses that reach a rough maximum diameter of 15 mm. 

When the first callus cells are inseminated, they are arranged into an array of **45** within a single petri dish. After a few weeks, these callus grow to around 1-2 mm, or about the size of one Nerd candy. The callus must then be transferred to a new petri dish into a wider-spaced array of **30** per dish as to prevent each individual mass from growing into each other and touching.

This process then repeats one more time after a few weeks, when the callus grow to the size of a pea. The final transfer goes from the array of 30 into an even wider-spaced array of **20**.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/transfer_1.png" class="rounded z-depth-1" style="width: 100%; height: 200px; object-fit: cover;" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/transfer_2.png" class="rounded z-depth-1" %}
    </div>
</div>

We were told that the research scientists process over *100,000* petri dishes of this type every year. Obviously, this would be tedious and mind-numbing for anyone, so our task was to automate this work for the scientists. The primary constraints of the project were:

- A budget of $1000
- The total footprint should stay roughly within 30 x 20 x 35 inches, but this isn't a hard limit.
- The device should be able to pick up different sizes of samples (anywhere from 1 mm to 15 mm).
- Consideration must be given to sterilization.

 *How* we automated the process was entirely up to us. For our team (and most of the other 5 teams), we wanted to completely automate petri dish handling and minimize any human intervention. Ideally, the final prototype would only require the user to insert input dishes callus filled dishes and brand new dishes for the callus to be transferred into, and the device would then output dishes filled with the transferred callus and eject empty dishes to be disposed.

## Final Prototype


<div class="row mt-3 ">
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/SD_FULL_CAD.png" class="rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0 fixed-height-row">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/timelapse.gif" class="rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    (LEFT) Full CAD model of final device. (RIGHT) Timelapse of prototype in operation.
</div>

With our final device we were able to achieve transfer times comparable to a human operator, ~98% reliability, fully automate the petri dish handling, and stay under our $1000 budget. The main functional elements of our final device are:

- 2 parallel carriages for holding and moving the petri dishes during transfer, defined as our x-direction degree of freedom (DOF).
- 1 gantry above the carriages to allow movement between the two parallel carriages / creating the necessary y-direction DOF.
- 1 gripper mechanism attached to the gantry, which contains the gripper itself, a cam-operated z-direction DOF, as well as the camera assembly for the computer vision system.
- 2 "de-lidding" mechanisms along each side of the carriages for removing and holding the petri dish lids.
- 4 lifts for moving dishes between the carriages and the storage stacks, allowing storage of up to 25 input and output dishes at one time. A "shudder" mechanism (similar to the aperture of a camera) is used to grip and hold the petri dishes at the bottom of the stacks.
- 1 off-the-shelf bead sterilizer used for sterilizing the gripper-callus contact points during operation.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/gripper_vid.mp4" class="rounded z-depth-1 w-100" style="width: 50%;" autoplay=true loop=true muted=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/delidder.mp4" class="rounded z-depth-1 w-100" autoplay=true loop=true muted=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/shudder.mp4" class="rounded z-depth-1 w-100" autoplay=true loop=true muted=true %}
    </div>
</div>

<div class="caption">
    From left to right, the gripper, shudder, and de-lidder mechanisms can be seen in operation.
</div>

## Design Approach

During early phases, we decided on a few overall guiding principles for how we were to design the machine, especially in the context of the competition: t

1. Automating the entire process was top priority (as stated above).

2. Design subsystems for modularity and simplicity to aid as much as possible in overall reliability and manufacturing complexity.

3. Because of the size of the budget ($1000), limit the amount of metal / precision components and 3D print as much as possible.

I believe point #2 was one of the main reasons that we ended up winning with our design. While the other teams designed systems that would have extremely fast transfer times *in theory* (e.g. the 2nd and 3rd place winner's designs were a 5-bar linkage gripper and a delta robot, respectively), the required complexity of those designs, mechanically and controls-wise, led to far more gremlins and last-minute headaches.

Point #3 is almost self-evident given the size and timeline of the project, but it should be noted. A lot of thought was put into creating mechanisms that needed to be precise in operation while being robust to the limitations of 3D printing.

The aspects that I worked on from start to finish were the gripper assembly and the control system for the entire machine, so I'll quickly go over those design aspects.

## Gripper and Z-Cam Mechanism

Before designing the gripper, I tried to find solutions to comparable problems within the life sciences. Most of what I found was too complex or too expensive, and would take resources away from other subsystems. Fortunately, I managed to find an older [research paper](https://www.jircas.go.jp/sites/default/files/publication/jarq/30-4-213-220_0.pdf) published at The University of Tokyo in 1996 that used 2 separate sheet metal plates as tweezers for very small and fragile (~1 mm Orchid Protocorm) objects [1]. The paper actuated these plates using shape memory alloy (SMA) wire. By running a variable amount of current through the wire, the scientists could adjust how much the SMA wire pulled on the plates and thus fine-tune the pressure the plates put on the objects.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/papmfpm/gripper_CAD.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <p>
         Our gripper uses  similar “tweezer-like” plate grippers made from thin sheet metal that open and close to grip and release calluses. The full assembly picture that I stole from our final report is adjacent, excluding springs for clarity--they can be seen in the above gif. Rather than use SMA wire, the plates are opened using fishing line wound around guides (<strong>2.l</strong>) and connected to a servo via a linkage (<strong>2.i</strong>) which separates the plates when rotated.</p>
        <br/>
        The entire callus gripper has a single DoF in z-direction, modulated via a servo, cam, and return springs. This provided 20 mm of travel--enough to raise callus over the edge of petri dishes and place them firmly into the medium of the next petri dish.
    </div>
</div>

I went with a cam mechanism as opposed to a typical lead-screw z-axis as we didn't need that level of precision or length for the z-axis. The cam mechanism is also much faster and light than a stepper motor + lead assembly.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/z-cam.png" class="rounded z-depth-1" %}
    </div>
</div>

## Control System

In total, the machine uses 11 stepper motors, 4 servos, and 2 solenoids. The brain of the machine is a Raspberry Pi 4. A BIGTREETECH Octopus V1.1 Control board was used for controlling 8 stepper motors--all 3 of the main machine axes and petri lifts--as well as all servos and solenoids. The Octopus is typically used for upgrading 3D printers, but can be repurposed for general automation projects. The remaining 3 stepper motors for the shudders were controlled via a Raspberry Pi Pico (RP2040) and TMC2209 drivers wired through a spare breadboard I had. A full wiring diagram is below for those interested.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/control_system.png" class="rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Full wiring diagram for entire machine.
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/system_arch.png" class="rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hardware / Software System Architecture / Flow diagram
</div>

Above is a flow diagram for the overall system architecture. The role of each software element is explained below:

- **Klipper** - Firmware for Octopus Control Board and RP2040 MCU. Like the Octopus Board, Klipper is typically used for 3D printing machines, but can be repurposed other projects. Parses G-Code commands to control defined machine kinematics/axes and all individual stepper motors/stepper drivers, servos, and solenoids.

- **Moonraker** - Python 3 web server that exposes Klipper APIs to external clients. Allows communication between frontend GUI (MainsailOS in this case), and Python scripts stored on the Raspberry Pi.

- **MainSail** - Web Interface / UI for interacting with Klipper. Configuration files and logs for the entire machine can be easily accessed on a web browser from a computer on the same network as the Raspberry Pi.

- **Transfer_Main.py** - Main script that creates G-Code from parsed camera data. Allows users to specify the type of transfer and amount of dishes to be processed.

- **Callus_Finder.py** - Script containing custom camera vision algorithm that pre-processes and filters raw images, to be called as desired in Transfer_Main. 

## Machine Vision

I'll touch briefly on the detection system for the machine. Our camera was a V3 Raspberry Pi camera, mounted on the bottom side of the Y-Gantry, shown in the image below (**1.k**). 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/papmfpm/camera_assembly.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        Callus_Finder.py, mainly written my my teammate Garett Fox, searches for the petri dish within a specified region of interest, using OpenCV blur, Canny thresholding, and Hough Transform to locate the dish edges. The located dish is then used as a boundary for searching for calluses and for determining absolute callus position coordinates. 
        <br/>
        <br/>
        Calluses are detected using OpenCV Gaussian blur, finding contours, and filtering via a convex Hull circularity filter. The effective moments of each identified callus region are calculated to find the centroid of each callus, which are converted to device coordinates using measured offsets and a measured pixel to millimeter ratio.
    </div>
</div>

The coordinates are output from the script such that Transfer_Main can generate G-Code for device motion to complete the transfers.

For testing, all teams decided on using peppercorn (~1-3 mmm) and frozen peas (~10-15 mm) as callus analog. The medium used within the real petri dishes is proprietary and could not be provided to us, so we used Jell-O as a stand-in. 

Shown below are the identification images output by our Callus Finder script. Both of these are examples where the callus analog rolled together after we placed them in our petri dish--this was mainly due to Jell-O not being an ideal stand-in for the real medium, which has a bit of sticky-ness to it. All failed transfers were due to the camera algorithm identifying 2 callus as 1.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/papmfpm/callus_detect.png" class="rounded z-depth-1" %}
    </div>
</div>

A lot of cool design details are missing from this post for the rest of this machine, but it would quickly turn into a book if I explained everything. I'm super happy with how the project turned out and had a great time working with the rest of the team.

---
