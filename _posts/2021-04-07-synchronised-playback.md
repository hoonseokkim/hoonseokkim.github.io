I have experience that when I watch football game, our neighbour starts to yell and I can understand why they yelled a few seconds later.

This is because of a few seconds delay between me and my neighbour.

To minimise this delay, MPEG-DASH introduces suggested presentation delay.

This suggested presentation delay feature is only applied on live contents. Live contents in DASH mean **MPD@type** is **dynamic**.

Literally suggested presentation delay gives delay of presentation time stamp on each frame of the contents.

Client can set suggested presentation delay forcely even if suggested presentation delay doesn't exist on mpd.

In this way, HLS also can support sychronised playback if **EXT-X-PROGRAM-DATE-TIME** exists in the playlist.

To synchronise with each devices, client should also consider server time value because system time of each devices could vary. Client could calculate server time value using Date header field of http from content server. Since the smallest value of Date header is seconds, limitation of synchronised playback is a second.

If client tries to synchronise with multiple players on a device, using system time is more accurate than using Date header field of http.
