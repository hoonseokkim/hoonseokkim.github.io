If HLS doesn't have **EXT-X-ENDLIST** tag, then it is live contents.

**EXT-X-TARGETDURATION** specifies maximum segment duration of media playlist.

Also HLS specification mentioned like below.

_When a client loads a Playlist file for the first time or reloads a
Playlist file and finds that it has changed since the last time it
was loaded, **the client MUST wait for at least the target duration
before attempting to reload the Playlist file again**, measured from
the last time the client began loading the Playlist file._

And here is the problem.

Client can always seek to the latest segment of the playlist.

If clients seek to the latest segment when playlist is updated and duration of the latest segment is less than target duration, buffering event is inevitable.

This buffering event can not be removed even if the lowest bandwidth track is selected.

Best solution would be to set **EXT-X-TARGETDURATION** close to **EXTINF** but this also can't fully avoid buffering event.
