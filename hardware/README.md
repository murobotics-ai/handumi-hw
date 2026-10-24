# Hardware

This folder contains the HandUMI printable hardware.

HandUMI is worn on the hand to record wrist-view video, gripper width, and
controller pose. It is matched to the robot, not the other way around: the
target robot keeps its installed parallel-jaw gripper, and HandUMI carries a
printed tip shaped like that gripper.

## Folder Layout

Printable files live in `STL/`, and editable CAD sources for every part live
in `STEP/`:

```text
STL/
|-- left_handumi/   # Left-hand HandUMI parts
|-- right_handumi/  # Right-hand HandUMI parts
`-- gripper_tips/   # Robot-specific detachable tips, one folder per robot
    |-- AgileX-Piper/
    |-- ARX-X5-2023/
    |-- Dream-Gripper/
    |-- Trossen-WidowXAI/
    `-- UMI-Gripper/

STEP/
|-- left_handumi/   # STEP sources for the left-hand parts
|-- right_handumi/  # STEP sources for the right-hand parts
`-- gripper_tips/   # STEP sources for the tips, for custom adjustments
    |-- AgileX-Piper/
    |-- ARX-X5-2023/
    |-- Dream-Gripper/
    |-- Trossen-WidowXAI/
    `-- UMI-Gripper/
```

## Calibration Board

`calibration/charuco_5x7_30mm_A4.pdf` is the ChArUco board that
`handumi calibrate spatial` expects (`opencv_charuco_5x7_30mm_v1`: 5 × 7
squares, `DICT_5X5_100`, 30 mm squares, 15 mm markers). Print it on A4 at 100%
(actual size, no fit-to-page), check that both scale bars measure 100 mm, and
mount it flat on a rigid backing.

## Modular Gripper Tip

HandUMI is modular: the body, camera mount, servo, and tracking mount stay the
same, while the detachable gripper tip changes to match the target robot
gripper.

Currently supported grippers:

- AgileX Piper (`STL/gripper_tips/AgileX-Piper/`)
- ARX X5 2023 (`STL/gripper_tips/ARX-X5-2023/`)
- Dream Gripper TRLC (`STL/gripper_tips/Dream-Gripper/`)
- Trossen WidowX AI (`STL/gripper_tips/Trossen-WidowXAI/`)
- UMI Gripper (`STL/gripper_tips/UMI-Gripper/`)

Any robot with a comparable parallel-jaw gripper can be supported by designing
and printing a matching tip. Start from the STEP sources in
`STEP/gripper_tips/` if you need to adjust a tip or adapt it to a new gripper.
STEP sources for the full left/right bodies are also available in
`STEP/left_handumi/` and `STEP/right_handumi/` for custom modifications
(e.g. refitting the finger cradles to another operator's hand).

## Print Guide

- PLA is the default material for early builds.
- For a left HandUMI, print the complete `STL/left_handumi/` folder.
- For a right HandUMI, print the complete `STL/right_handumi/` folder.
- Depending on your robotic arm with a parallel gripper, print the
  corresponding gripper tips from `STL/gripper_tips/`. If you want to make
  adjustments, modify the STEP sources in `STEP/gripper_tips/` and export your
  own STLs.

Detailed orientation, support, layer height, and infill settings will be added
in a future update.

## Assembly

Follow the step-by-step [Assembly Guide](HandUMI_Assembly_Guide.pdf) (PDF,
12 steps with CAD views). It walks through the left-hand unit; the right-hand
unit mirrors it with the `right_handumi` parts.

> **Note:** HandUMI uses only M2 and M3 fasteners. In step 10 (camera
> support), use two M2 × 8 socket-head screws and two M2 hex nuts instead of
> the M2.5 parts named in the guide.

HandUMI assembly is organized around three modules:

1. Finger-worn body and thumb/index-middle finger cradle.
2. Camera and tracking mounts.
3. Detachable robot-specific gripper tip.

To collect data for a different arm, keep the main body unchanged and swap
only the gripper tip. The robot itself needs no hardware changes.
