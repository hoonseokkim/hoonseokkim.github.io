I have experience that when I watch football game, our neighbour starts to yell and I can understand why they yelled a few seconds later.

This is because of a few seconds delay between me and my neighbour.

To minimise this delay, MPEG-DASH introduces **MPD@suggestedPresentationDelay**.

This feature is only applied on live contents. Live contents in DASH mean **MPD@type** is **dynamic**.

Literally **MPD@suggestedPresentationDelay** gives delay of presentation time on each frame of the contents. If player supports SPD feature, it's also possible to set suggested presentation delay forcely even if suggested presentation delay doesn't exist on mpd.

In this way, HLS also can support sychronised playback if **EXT-X-PROGRAM-DATE-TIME** exists in the playlist.

In order to minimise the delay, player should also consider server time value because system time of each devices could vary. Player could calculate server time value using Date field of HTTP header given by content server. Since the smallest value of Date field of HTTP Header is a second, limitation of synchronised playback by using HTTP header is a second.

To reduce delay more, delay from decoder itself might be also considered.

If client tries to synchronise with multiple players on a device, using system time might be more accurate than using Date field of HTTP header.
