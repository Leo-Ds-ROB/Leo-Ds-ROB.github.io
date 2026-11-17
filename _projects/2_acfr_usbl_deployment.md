---
layout: page
title: Automated USBL deployment for a BlueBoat USV
description: ACFR, University of Sydney, 2025 · Dual lead-screw mechanism to lower and retract a USBL transducer autonomously
img: assets/img/acfr-final-assembly.jpg
importance: 2
category: research internships
related_publications: false
---

**Context.** Research internship (April–August 2025) in the Marine Group of the **Australian Centre for Field Robotics (ACFR)**, University of Sydney. The lab uses a Blue Robotics BlueBoat as a compact surface platform; fitted with a USBL (Ultra-Short Baseline) acoustic transceiver, it can track underwater vehicles such as AUVs, where GPS is not available.

**Problem.** A previous student had built a manual mount for the USBL transducer. It was mechanically sound, but the transducer had to be lowered and raised by hand before and after each mission, which defeats the purpose of an autonomous vessel and puts sensitive equipment at risk during handling.

**Goal.** Design, prototype and validate a self-contained mechanism that lets the BlueBoat lower the USBL at least 35 cm below the hull and retract it on its own, powered from the boat's 16 V battery, compact, seaworthy and easy to maintain.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/acfr-final-assembly.jpg" title="Final prototype on the BlueBoat" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/acfr-lab-tank.jpg" title="Prototype in the lab tank" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: the motorised deployment system mounted on the BlueBoat. Right: the prototype during water-tank testing at ACFR.
</div>

## What I did

- **Concept selection.** Reviewed the previous manual design, defined requirements (≥ 35 cm stroke, automated motion, 16 V supply, saltwater-resistant parts, easy maintenance) and compared an electric linear actuator with a stepper motor + lead screw. Chose the lead-screw solution for its cost, sourcing, maintainability and control flexibility.
- **Sizing.** Estimated a 4 kg moving load, computed the required torque (0.036 N·m with a 2 mm pitch, 0.09 N·m with 5 mm), speed (~420 rpm for 35 cm in 10 s with a 5 mm pitch) and power (~19 W electrical), then benchmarked IP68 stepper motors from several suppliers.
- **Electronics.** Two IP68 NEMA 23 stepper motors (1.89 N·m holding torque), DM542T digital drivers, a 16 → 24 V DC-DC boost converter and a Teensy 4.0 generating step/direction signals.
- **Mechanical design (Fusion 360).** Rebuilt the existing mount in CAD, reinforced the frame with additional T-slot aluminium extrusions, and designed a symmetric **dual lead-screw** architecture: one motor per screw, KFL flange bearings, jaw couplings, PETG motor brackets with a three-point mounting, and a custom connector linking the screw nuts to the existing USBL platform.
- **Fabrication and assembly.** Cut and drilled the extrusions, tapped threads by hand, 3D-printed the PETG parts on a Prusa XL, then assembled and aligned the motion system on the boat. Fixed a friction issue by re-aligning the upper extrusions, and reprinted a broken bracket.
- **Testing.** Ran a verification checklist, then water-tank trials: one hour of continuous cycles, full-stroke rigidity checks with added 1 kg loads to mimic hydrodynamic forces, fastening checks and wave agitation.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-previous-design.jpg" title="Previous manual USBL mount" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-cad-old-frame.jpg" title="Original frame (CAD)" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-cad-reinforced-frame.jpg" title="Reinforced frame (CAD)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Starting point: the previous manual mount (left), rebuilt in CAD (middle) and reinforced with extra T-slot extrusions to carry the motors (right).
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-cad-lead-screw.jpg" title="Lead-screw drive (CAD)" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-cad-motor-mounts.jpg" title="Motor mounts on the frame (CAD)" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-cad-connector.jpg" title="Connector to the USBL platform (CAD)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fusion 360 design: IP68 motor, jaw coupling, lead screw and KFL bearing (left), PETG motor brackets on the reinforced frame (middle), and the custom connector between the screw nut and the USBL platform (right).
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-motor-mounted.jpg" title="Stepper motor on its bracket" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-bearing.jpg" title="Flange bearing on the payload bracket" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-connector.jpg" title="Connector fitted to the USBL platform" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Assembly on the boat: stepper motor on its 3D-printed bracket, flange bearing at the base of the lead screw, and the connector fitted to the moving USBL platform.
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/acfr-fully-deployed.jpg" title="USBL fully deployed" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    USBL platform at full stroke, 35 cm below the hull.
</div>

## Results

| Requirement | Result |
| :-- | :-- |
| Automated deployment and retraction | Achieved, open-loop step/direction control from a Teensy 4.0 |
| Stroke ≥ 35 cm below the hull | 350 mm reached on every cycle |
| Deployment time (target 10–20 s) | About 20 s for the full stroke |
| Rigidity at full extension | No lateral play or deformation, including with added 1 kg loads |
| Repeatability | About 50 cycles over one hour without mechanical failure; a few millimetres of drift by the end |
| Watertightness | No water ingress in the IP68 components |

The drift was traced to the jaw couplings progressively loosening and introducing backlash. Identified next steps: couplings with dual set screws and thread-locker, limit switches or linear encoders for closed-loop control, electronics moved into IP68 enclosures inside the hull, integration with the mission-planning software, and open-water trials.

**Tools:** Fusion 360 · 3D printing (PETG, Prusa XL) · T-slot aluminium · IP68 stepper motors · DM542T drivers · DC-DC boost converter · Teensy 4.0 (Arduino) · BlueBoat
