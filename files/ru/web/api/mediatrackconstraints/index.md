---
title: MediaTrackConstraints
slug: Web/API/MediaTrackConstraints
tags:
  - API
  - Constraints
  - Dictionary
  - Interface
  - Media
  - Media Capture and Streams API
  - Media Streams API
  - MediaTrackConstraints
  - NeedsTranslation
  - Reference
  - Screen Sharing
  - Screen Sharing API
  - Sharing
  - TopicStub
  - WebRTC
  - screen
translation_of: Web/API/MediaTrackConstraints
---
{{APIRef("Media Capture and Streams")}}

The **`MediaTrackConstraints`** dictionary is used to describe a set of capabilities and the value or values each can take on. A constraints dictionary is passed into {{domxref("MediaStreamTrack.applyConstraints", "applyConstraints()")}} to allow a script to establish a set of exact (required) values or ranges and/or preferred values or ranges of values for the track, and the most recently-requested set of custom constraints can be retrieved by calling {{domxref("MediaStreamTrack.getConstraints", "getConstraints()")}}.

For each constraint, you can typically specify an exact value you need, an ideal value you want, a range of acceptable values, and/or a value which you'd like to be as close to as possible. The specifics vary somewhat depending on the type of the constrainable property.

To learn more about how constraints work, see [Capabilities, constraints, and settings](/ru/docs/Web/API/Media_Streams_API/Constraints).

## Properties

Some combination—but not necessarily all—of the following properties will exist on the object. This may be because a given browser doesn't support the property, or because it doesn't apply. For example, because {{Glossary("RTP")}} doesn't provide some of these values during negotiation of a WebRTC connection, a track associated with a {{domxref("RTCPeerConnection")}} will not include certain values, such as {{domxref("MediaTrackConstraints.facingMode", "facingMode")}} or {{domxref("MediaTrackConstraints.groupId", "groupId")}}.

### Properties of all media tracks

- {{domxref("MediaTrackConstraints.deviceId", "deviceId")}}
  - : A {{domxref("ConstrainDOMString")}} object specifying a device ID or an array of device IDs which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.groupId", "groupId")}}
  - : A {{domxref("ConstrainDOMString")}} object specifying a group ID or an array of group IDs which are acceptable and/or required.

### Properties of audio tracks

- {{domxref("MediaTrackConstraints.autoGainControl", "autoGainControl")}}
  - : A {{domxref("ConstrainBoolean")}} object which specifies whether automatic gain control is preferred and/or required.
- {{domxref("MediaTrackConstraints.channelCount", "channelCount")}}
  - : A {{domxref("ConstrainLong")}} specifying the channel count or range of channel counts which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.echoCancellation", "echoCancellation")}}
  - : A {{domxref("ConstrainBoolean")}} object specifying whether or not echo cancellation is preferred and/or required.
- {{domxref("MediaTrackConstraints.latency", "latency")}}
  - : A {{domxref("ConstrainDouble")}} specifying the latency or range of latencies which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.noiseSuppression", "noiseSuppression")}}
  - : A {{domxref("ConstrainBoolean")}} which specifies whether noise suppression is preferred and/or required.
- {{domxref("MediaTrackConstraints.sampleRate", "sampleRate")}}
  - : A {{domxref("ConstrainLong")}} specifying the sample rate or range of sample rates which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.sampleSize", "sampleSize")}}
  - : A {{domxref("ConstrainLong")}} specifying the sample size or range of sample sizes which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.volume", "volume")}}
  - : A {{domxref("ConstrainDouble")}} specifying the volume or range of volumes which are acceptable and/or required.

### Properties of image tracks

- {{domxref("MediaTrackConstraints.whiteBalanceMode","whiteBalanceMode")}}
  - : A {{jsxref("String")}} specifying one of `"none"`, `"manual"`, `"single-shot"`, or `"continuous"`.
- {{domxref("MediaTrackConstraints.exposureMode","exposureMode")}}
  - : A {{jsxref("String")}} specifying one of `"none"`, `"manual"`, `"single-shot"`, or `"continuous"`.
- {{domxref("MediaTrackConstraints.focusMode","focusMode")}}
  - : A {{jsxref("String")}} specifying one of `"none"`, `"manual"`, `"single-shot"`, or `"continuous"`.
- {{domxref("MediaTrackConstraints.pointsOfInterest","pointsOfInterest")}}
  - : The pixel coordinates on the sensor of one or more points of interest. This is either an object in the form { x:_value_, y:_value_ } or an array of such objects, where _value_ is a double-precision integer.
- {{domxref("MediaTrackConstraints.expsureCompensation","exposureCompensation")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying f-stop adjustment by up to ±3.
- {{domxref("MediaTrackConstraints.colorTemperature","colorTemperature")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying a desired color temperature in degrees kelvin.
- {{domxref("MediaTrackConstraints.iso","iso")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying a desired iso setting.
- {{domxref("MediaTrackConstraints.brightness","brightness")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying a desired brightness setting.
- {{domxref("MediaTrackConstraints.contrast","contrast")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying the degree of difference between light and dark.
- {{domxref("MediaTrackConstraints.saturation","saturation")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying the degree of color intensity.
- {{domxref("MediaTrackConstraints.sharpness","sharpness")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying the intensity of edges.
- {{domxref("MediaTrackConstraints.focusDistance","focusDistance")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying distance to a focused object.
- {{domxref("MediaTrackConstraints.zoom","zoom")}}
  - : A {{domxref("ConstrainDouble")}} (a double-precision integer) specifying the desired focal length.
- {{domxref("MediaTrackConstraints.torch","torch")}}
  - : A {{jsxref("Boolean")}} defining whether the fill light is continuously connected, meaning it stays on as long as the track is active.

### Properties of video tracks

- {{domxref("MediaTrackConstraints.aspectRatio", "aspectRatio")}}
  - : A {{domxref("ConstrainDouble")}} specifying the video aspect ratio or range of aspect ratios which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.facingMode", "facingMode")}}
  - : A {{domxref("ConstrainDOMString")}} object specifying a facing or an array of facings which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.frameRate", "frameRate")}}
  - : A {{domxref("ConstrainDouble")}} specifying the frame rate or range of frame rates which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.height", "height")}}
  - : A {{domxref("ConstrainLong")}} specifying the video height or range of heights which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.width", "width")}}
  - : A {{domxref("ConstrainLong")}} specifying the video width or range of widths which are acceptable and/or required.
- {{domxref("MediaTrackConstraints.resizeMode", "resizeMode")}}
  - : A {{domxref("ConstrainDOMString")}} object specifying a mode or an array of modes the UA can use to derive the resolution of a video track. Allowed values are `none` and `crop-and-scale`. `none` means that the user agent uses the resolution provided by the camera, its driver or the OS. `crop-and-scale` means that the user agent can use cropping and downscaling on the camera output in order to satisfy other constraints that affect the resolution.

### Properties of shared screen tracks

These constraints apply to `MediaTrackConstraints` objects specified as part of the {{domxref("DisplayMediaStreamConstraints")}} object's {{domxref("DisplayMediaStreamConstraints.video", "video")}} property when using {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} to obtain a stream for screen sharing.

- {{domxref("MediaTrackConstraints.cursor", "cursor")}}

  - : A {{domxref("ConstrainDOMString")}} which specifies whether or not to include the mouse cursor in the generated track, and if so, whether or not to hide it while not moving. The value may be a single one of the following strings, or an array of them to allow the browser flexibility in deciding what to do about the cursor.

    - `always`
      - : The mouse is always visible in the video content of the {domxref("MediaStream"), unless the mouse has moved outside the area of the content.
    - `motion`
      - : The mouse cursor is always included in the video if it's moving, and for a short time after it stops moving.
    - `never`
      - : The mouse cursor is never included in the shared video.

- {{domxref("MediaTrackConstraints.displaySurface", "displaySurface")}}

  - : A {{domxref("ConstrainDOMString")}} which specifies the types of display surface that may be selected by the user. This may be a single one of the following strings, or a list of them to allow multiple source surfaces:

    - `application`
      - : The stream contains all of the windows of the application chosen by the user rendered into the one video track.
    - `browser`
      - : The stream contains the contents of a single browser tab selected by the user.
    - `monitor`
      - : The stream's video track contains the entire contents of one or more of the user's screens.
    - `window`
      - : The stream contains a single window selected by the user for sharing.

- {{domxref("MediaTrackConstraints.logicalSurface", "logicalSurface")}}
  - : A {{domxref("ConstrainBoolean")}} value which may contain a single Boolean value or a set of them, indicating whether or not to allow the user to choose source surfaces which do not directly correspond to display areas. These may include backing buffers for windows to allow capture of window contents that are hidden by other windows in front of them, or buffers containing larger documents that need to be scrolled through to see the entire contents in their windows.

## Specifications

| Specification                                                                                | Status                                   | Comment                 |
| -------------------------------------------------------------------------------------------- | ---------------------------------------- | ----------------------- |
| {{SpecName('Media Capture', '#dom-mediatrackconstraints')}}             | {{Spec2('Media Capture')}}     | Initial definition.     |
| {{SpecName('MediaStream Image', '#mediatrackconstraintset-section')}} | {{Spec2('MediaStream Image')}} | Adds image constraints. |

## Browser compatibility

{{Compat}}

## See also

- [Media Capture and Streams API](/ru/docs/Web/API/Media_Streams_API)
- [Capabilities, constraints, and settings](/ru/docs/Web/API/Media_Streams_API/Constraints)
- [Screen Capture API](/ru/docs/Web/API/Screen_Capture_API)
- [Using the Screen Capture API](/ru/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- {{domxref("MediaDevices.getUserMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack.getSettings()")}}
