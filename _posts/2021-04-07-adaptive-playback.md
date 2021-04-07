To support various tracks in the playlist or mpd without flickering, decoder needs special feature.

For Android, this feature is called **FEATURE_AdaptivePlayback** in media codec, which let client check whether or not new track can be supported without reinitializing decoder.

For iOS, there is video tool box api called **VTDecompressionSessionCanAcceptFormatDescription**, which is similar with above feature **FEATURE_AdaptivePlayback**.

The only difference is that Android directly asks to hardware decoder and iOS needs **CMFormatDescriptionRef** to call **VTDecompressionSessionCanAcceptFormatDescription**.

Of course even if decoder supports above feature, there is still limitation like different video stream format(AnnexB to AVCC), clear contents to encrypted contents, different codecs, or etc.

If decoder doesn't support this feature, decoder should be reinitialised and this causes flickering when track is changed.
