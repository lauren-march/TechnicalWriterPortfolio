# Continuous Calibration

This page provides detailed information on the continuous calibration feature, which can be enabled from the [Calibration pane](../../motive-ui-panes/calibration-pane). For additional Continuous Calibration features, please see the [Continuous Calibration (Info Pane)](continuous-calibration-info-pane) page.

## Overview

The Continuous Calibration feature ensures your system always remains optimally calibrated, requiring no user intervention to maintain the tracking quality. It uses highly sophisticated algorithms to evaluate the quality of the calibration and the triangulated marker positions. Whenever the tracking accuracy degrades, Motive will automatically detect and update the calibration to provide the most globally optimized tracking system.

### Key Features

* **Ease of use.** This feature provides much easier user experience because the capture volume will not have to be re-calibrated as often, which will save a lot of time. You can simply enable this feature and have Motive maintain the calibration quality.
* **Optimal tracking quality.** Always maintains the best tracking solution for live camera systems. This ensures that your captured sessions retain the highest quality calibration. If the system receives inadequate information from the environment, the calibration with not update and your system never degrades based on sporadic or spurious data. A moderate increase in the number of real optical tracking markers in the volume and an increase in camera overlap improves the likelihood of a higher quality update.
* **Works with all camera types.** Continuous calibration works with all OptiTrack camera models.

### Requirements

For continuous calibration to work as expected, the following criteria must be met:

* **Live Mode Only.** Continuous calibration only works in [Live mode](../data-recording).
* **Markers Must Be Tracked.** Continuous calibration looks at tracked reconstructions to assess and update the calibration. Therefore, at least some number of markers must be tracked within the volume.
* **Majority of Cameras Must See Markers.** A majority of cameras in a volume needs to receive some tracking data within a portion of their field of view in order to initiate the calibration process. Because of this, traditional perimeter camera systems typically work the best. Each camera should additionally see at least 4 markers for optimal calibration. If not all the cameras see the markers at the same time, anchor markers will need to be set up to improve the calibration updates.

![Whenever possible, continuous calibration seeks to maintain and improve convergence of the tracked rays throughout the volume.](https://content.gitbook.com/content/M6DLKAZnkJZyY3rN2hqt/blobs/bcplgZy87fhdYEZSoJoN/image.png)

## How to Use

To enable Continuous Calibration, calibrate the camera system first and enable the Continuous Calibration setting at the bottom of the [Calibration pane](../../motive-ui-panes/calibration-pane). Once enabled, Motive continuously monitors the residual values in captured marker reconstructions, and when the updated calibration is better than the existing one, it will get updated automatically. Please note that at least four (default) marker samples must be being tracked in the volume for the continuous calibration to work. You will also be able to monitor the sampling progress and when the calibration has been last updated.

{% hint style="warning" %}
Please see the [Continuous Calibration (Info Pane)](continuous-calibration-info-pane) page for additional features.&#x20;
{% endhint %}

![Continuous calibration enabled under the Calibration pane.](https://content.gitbook.com/content/M6DLKAZnkJZyY3rN2hqt/blobs/qWk8pBOA5kBBxVwrFAZA/image.png)

## Anchor Markers

Anchor markers further improve the continuous calibration. When properly configured, anchor markers establish a known point-of-reference for continuous calibration updates, especially on systems that consists of multiple sets of cameras that are separated into different tracking areas, by obstructions or walls, without camera view overlap. Anchor markers provide extra assurance that the global origin will not shift during each update, which the continuous calibration feature checks for as well.

### Active Anchor Markers

Active markers are best to use for anchors due to their unique active IDs, which improve accuracy, remove ambiguity, and enhance continuous calibration all around.

* Cameras will always correctly identify an active marker even when no other markers are visible or after an occlusion. This helps the system calibrate more frequently, and to quickly adjust after more significant disturbances.&#x20;
* Anchor markers are critical to maintaining a single calibration throughout a partitioned volume. Active markers ensure that the cameras can correctly identify each anchor marker location.
* Active markers allow bumped cameras to update faster and more accurately, and to recover from larger disturbances than passive markers.

{% hint style="info" %}
For continuous calibration to work, It's important to have multiple markers visible to each camera, dispersed across a significant portion of that camera's field of view. This allows the system to more accurately determine the position and angle of the camera. This is true whether using active or passive markers.&#x20;
{% endhint %}

### Anchor Marker Setup

Follow the steps below for setting up the anchor marker in Motive:

**Adding Anchor Markers in Motive**

1. First, make sure the entire camera volume is fully [calibrated]() and prepared for marker tracking.
2. Place any number of markers in the volume to assign them as the anchor markers.
3. Make sure these markers are securely fixed in place within the volume. It's important that the distances between these markers do not change throughout the continuous calibration updates.
4. Open the [Calibration pane](../../motive-ui-panes/calibration-pane) and select the second page at the bottom to access the anchor marker feature.
5. In the 3D viewport, select the markers that are going to be assigned as anchors.
6. Click on _Add_ to add the selected markers as anchor markers.
7. Once markers are added as anchor markers, magenta spheres will appear around the markers indicating the anchors have been set.
8. Add more anchors as needed, again, it's important that these anchor markers do not move throughout the tracking. Also when the anchor markers need to be reset, whether if the marker was displaced, you can clear the anchor markers and reassign them.

<div><img src="https://content.gitbook.com/content/M6DLKAZnkJZyY3rN2hqt/blobs/kPBZLQLM39cxiGzAnVIP/image.png" alt="Access the second page at the bottom to show anchor marker feature."> <figure><img src="https://content.gitbook.com/content/M6DLKAZnkJZyY3rN2hqt/blobs/F9leslbGjXuitmbg8AWa/image.png" alt=""><figcaption><p>Anchor markers assigned in Motive.</p></figcaption></figure></div>

## Camera Partitions

For multi-room setups, it is useful to group cameras into partitions. This allows for Continuous Calibration to run in each individual room without the need for camera view overlap.&#x20;

### Properties Pane: Camera

From the Properties pane of a camera you can assign a Partition ID from the advanced settings.&#x20;

<figure><img src="https://content.gitbook.com/content/M6DLKAZnkJZyY3rN2hqt/blobs/mK4a4SENirASbCz1kUrL/image.png" alt=""><figcaption><p>Change Partition ID under Threshold in the Advanced Settings within the Properties pane. </p></figcaption></figure>

You'll want to assign all the cameras in the same room the same Partition ID. Once assigned these cameras will all contribute to Continuous Calibration for their particular space. This will help ensure the accuracy of Continuous Calibration for each individual space that is a part of the whole system.&#x20;

## Editing Camera Positions with Gizmo Tool

In the event that you need to manually adjust cameras in the 3D view, you can enable Editable in 3D View in [General Settings](../../motive-ui-panes/settings/settings-general). To access this setting, you'll need to select Show Advanced from the 3-dot more options dropdown at the top. This will populate a Calibration section on this window.&#x20;

<figure><img src="https://content.gitbook.com/content/M6DLKAZnkJZyY3rN2hqt/blobs/srveeZ8o9FcxmLbDoGAH/image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://content.gitbook.com/content/M6DLKAZnkJZyY3rN2hqt/blobs/ocNbxMmRToq21H2fa5K1/image.png" alt=""><figcaption></figcaption></figure>

This allows you to use the [Gizmo Tools](../assets/gizmo-tool-translate-rotate-and-scale) to Translate, Rotate, and Scale cameras to their desired locations.&#x20;
