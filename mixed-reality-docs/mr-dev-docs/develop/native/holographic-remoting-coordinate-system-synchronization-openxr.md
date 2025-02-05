---
title: Coordinate System Synchronization with Holographic Remoting and the OpenXR API
description: This page explains how Coordinate System Synchronization with Holographic Remoting and the OpenXR API works
author: vimusc
ms.author: vimusch
ms.date: 09/07/2021
ms.topic: article
keywords: HoloLens, HoloLens 2, mixed reality, MRTK, Mixed Reality Toolkit, augmented reality, virtual reality, mixed reality headsets, learn, tutorial, getting started, holographic remoting, openxr
---

# Coordinate System Synchronization with Holographic Remoting and the OpenXR API

With the OpenXR API, the user coordinate system is wrapped into a reference space of type ```XR_REMOTING_REFERENCE_SPACE_TYPE_USER_MSFT```.

>[!TIP]
>A simple example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
>Uncomment ```#define ENABLE_USER_COORDINATE_SYSTEM_SAMPLE``` inside the OpenXrProgramm.cpp and SamplePlayerMain.h files to enable the sample code.

>[!IMPORTANT]
>To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/main/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## Set and Update the User Coordinate System in the Player App

Holographic Remoting currently only supports writing a custom player with the Windows Mixed Reality API.
A player written with the Windows Mixed Reality API can be used with a OpenXR remote! Therefore, you have to set the User Coordinate System from the Windows Mixed Reality player.
For more information, see [Coordinate System Synchronization with Holographic Remoting and the Windows Mixed Reality API](holographic-remoting-coordinate-system-synchronization-wmr.md).

## Get the User Coordinate System in the Remote App

To create the user coordinate system in the remote app call ```xrCreateReferenceSpace``` with the ```XR_REMOTING_REFERENCE_SPACE_TYPE_USER_MSFT``` argument:

```cpp
xr::SpaceHandle space;
XrReferenceSpaceCreateInfo createInfo{XR_TYPE_REFERENCE_SPACE_CREATE_INFO};
createInfo.referenceSpaceType = static_cast<XrReferenceSpaceType>(XR_REMOTING_REFERENCE_SPACE_TYPE_USER_MSFT);
createInfo.poseInReferenceSpace = xr::math::Pose::Translation({0.0f, 0.0f, 0.0f});
CHECK_XRCMD(xrCreateReferenceSpace(m_session.Get(), &createInfo, space.Put()));
```

## See Also

* [Coordinate System Synchronization with Holographic Remoting Overview](holographic-remoting-coordinate-system-synchronization.md)
* [Coordinate System Synchronization with Holographic Remoting and the Windows Mixed Reality API](holographic-remoting-coordinate-system-synchronization-wmr.md)
