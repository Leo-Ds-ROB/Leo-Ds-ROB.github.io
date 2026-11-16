---
layout: page
title: Itsasdrone USV – sensing upgrade
description: AZTI, 2026 · GNSS diagnosis, dual-camera integration and 3D-printed camera mounts on a BlueBoat-based USV
img: assets/img/azti-images/azti-itsasdrone.jpg
importance: 1
category: research internships
related_publications: false
---

**Context.** End-of-studies internship (April–September 2026) at **AZTI**, a marine research centre in the Basque Country, Spain. Itsasdrone is AZTI's uncrewed surface vehicle: a Blue Robotics BlueBoat adapted to carry a Simrad WBT Mini / EK80 scientific echo sounder for fisheries and oceanographic surveys.

**Problem.** The platform was not reliable enough for routine autonomous missions. The GNSS position was missing or unstable, the onboard software had not been updated for more than three years, and with no onboard camera the operator had to keep the boat in direct line of sight.

**My role.** Return the vehicle to a reliable operational state and add onboard visual feedback, from diagnosis to mechanical design, integration and testing.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/azti-images/azti-itsasdrone.jpg" title="Itsasdrone at AZTI" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/azti-images/azti-overview.jpg" title="Upgraded Itsasdrone with two exploreHD cameras" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Itsasdrone, AZTI's BlueBoat-based USV. Right: the upgraded vehicle with its two exploreHD cameras on 3D-printed mounts.
</div>

## What I did

- **Clean software baseline.** Full BlueOS update and reconfiguration of the vehicle, so that new problems could be separated from legacy configuration issues.
- **GNSS diagnosis.** Ruled out sky visibility and cable interference, then traced the missing fix to a mismatch between the physical serial port used by the mRo GPS (u-blox NEO-M8N) and the port declared as GPS input in the autopilot. Rewiring and recalibrating the GPS/compass restored a coherent position.
- **Dual-camera integration.** Integrated two DeepWater Exploration exploreHD USB cameras through the dweOS extension and the Cockpit operator interface. Showed that powering them from the Raspberry Pi degraded GNSS reception, and fixed it with an externally powered USB hub fed from the boat batteries.
- **Mechanical design.** Built a simplified CAD model of the vehicle in Fusion 360, studied three camera layouts (front/rear, above-water + underwater, raised rear pole) and designed modular 3D-printed mounts for each.
- **Integration and testing.** Installed the mounts, an antenna mast extension and WetLink penetrators on the watertight enclosure, then ran bench, outdoor and watertightness tests.
- **Latency investigation.** Analysed a variable command delay using network measurements, ArduPilot logs (RCIN vs RCOU) and MAVLink messages (MANUAL_CONTROL vs SERVO_OUTPUT_RAW).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-gps-before.jpg" title="GNSS track before recalibration" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-gps-after.jpg" title="GNSS track after recalibration" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Static outdoor GNSS test before (left) and after (right) the serial-port fix and recalibration: the dispersed track with large jumps becomes compact and coherent.
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-gnss-vs-cameras.png" title="GNSS satellites vs. number of cameras" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Maximum number of satellites tracked depending on how many cameras were powered directly by the Raspberry Pi. An externally powered USB hub removed the conflict.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-cad-model.jpg" title="Simplified CAD model of Itsasdrone" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-cad-underwater.jpg" title="Underwater camera mount (CAD)" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-cad-pole.jpg" title="Raised pole camera mount (CAD)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Fusion 360 model of the vehicle used to study camera positions, with the underwater mount and the raised-pole mount.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-mount-underwater.jpg" title="Underwater camera mount installed" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-mount-upper.jpg" title="Upper camera mount installed" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-penetrators.jpg" title="WetLink penetrators on the enclosure" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    3D-printed mounts installed on the vehicle, and WetLink penetrators bringing the camera cables into the watertight enclosure.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="lazy" path="assets/img/azti-images/azti-dual-camera-test.jpg" title="Both camera streams and GNSS in Cockpit" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Validation in Cockpit: both camera streams running while the GNSS fix is maintained.
</div>

## Results

- **GNSS restored:** over 15 trials, about 18 satellites tracked, 1 Hz position updates and roughly 1 m observed accuracy.
- **Cameras and GNSS together:** both video streams ran continuously with the GNSS fix maintained.
- **Watertightness:** no water ingress through the new cable penetrators.
- **Latency characterised:** median 346 ms, mean 724 ms, max 1.29 s on the control link. Unstable networking was identified as a likely contributor; the full root cause remained open at the end of the internship.
- **Next steps identified:** on-water trials, RTK GNSS (u-blox ZED-X20P) for centimetre-level positioning, and a permanent, cleaner electronics layout.

**Tools:** BlueOS · ArduRover / ArduPilot · MAVLink · Cockpit · QGroundControl · Raspberry Pi 4 + Navigator · DWE exploreHD · Fusion 360 · 3D printing
