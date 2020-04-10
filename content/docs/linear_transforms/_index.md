---
title: "Linear Transform in 3D Slicer"
linkTitle: "Linear Transform in 3D Slicer"
weight: 3
description: 
type: docs
---

{{% pageinfo %}}
Ensure you are using <a href="https://download.slicer.org/" target="_blank">3D Slicer 4.10.2</a>.
{{% /pageinfo %}}

Naming Scheme for Fiducial Files
--------------------------------
* [VolumeID]\_[Contrast]\_[Rater]\_[N] (e.g. macaqueMNI_T1_JL_01)

  * **[VolumeID]** = the identifier for the volume on which you are performing the fiducial placements; for the tutorial it will be a well known macaque MRI templates:
    * Colin27: average of 25 adult macaque monkeys (18 Macaca Fascicularis, 7 Macaca Mulatta)
  * **[Contrast]** = T1
  * **[Rater]** = the unique identifier for the rater performing the fiducial placement; convention will be first initial and last name to prevent overlap
  * **[N]** = reference for fiducial placement session (helpful if performing placements more than once; starting with 1)

AC-PC Placement
---------------
Download assigned volume/template from github repository. Go to Markups Module and create markups list entitled **ACPC\_[VolumeID]\_[Contrast]\_[Rater]\_[N]**. Place **AC** and **PC** landmarks:

1. AC = anterior commissure (center)
2. PC = posterior commissure (center)

Create new AC-PC transform
--------------------------
Create a new markups list entitled **Fid32\_[VolumeID]\_[Contrast]\_[Rater]\_[N]**. Create a new markups list entitled **midline**.

To create a new AC-PC Transform you must place AC and PC fiducial markers in previous step.

1. Copy AC and PC markers from **ACPC** to the **midline** markups list.
2. Go back to the **midline** markups list and place a fiducial marker in the infracollicular sulcus (point 3)
3. Place another fiducial marker at the Genu of CC (point 19)
4. You should now have AC and PC in the **ACPC** markups list and AC, PC, infracollicular sulcus and Genu of CC in the **midline** markups list
5. Under modules select Registration --> Specialized --> ACPC Transform. 
6. In the Transform Panel, under ACPC Line select the **ACPC** markups list, under Midline select the **midline** markups list, and under Output transform select **"Create new linear transform as…"** and name it **Output transform**.
7. Click **apply** at the bottom of the window.
8. **Note: if the volume turns off** --> under modules go to Data. Beside the image volume select the ‘eye’ icon to turn the volume back on.
9. Next under Modules go to Transforms and under Active Transform dropdown tab select the create Output transform (if not already selected). 
10. Under Apply Transform select all 4 items (i.e **macaqueMNI**, **ACPC_macaqueMNI_T1_GG_0l**, **midline**, and **Fid32_macaqueMNI_T1_GG_0l**) and transfer them to the transformed side. 
