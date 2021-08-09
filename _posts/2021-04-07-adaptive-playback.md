To support various tracks in the playlist or mpd without flickering, decoder needs special feature.

For Android, this feature is called **FEATURE_AdaptivePlayback** in media codec, which gives information whether or not codec should be reinitialised. Sometimes, even if **FEATURE_AdaptivePlayback** is supported, some of HW decoder doesn't actually support the new track.

For iOS, there is VideoToolbox api called **VTDecompressionSessionCanAcceptFormatDescription**, which is similar with above feature **FEATURE_AdaptivePlayback**. It needs **CMFormatDescriptionRef** to call **VTDecompressionSessionCanAcceptFormatDescription**.

Of course even if decoder supports above feature, there is still limitation like different video stream format(AnnexB to AVCC), clear contents to encrypted contents, different codecs, or etc.

If decoder doesn't support this feature, decoder should be reinitialised and this causes flickering when track is changed.
