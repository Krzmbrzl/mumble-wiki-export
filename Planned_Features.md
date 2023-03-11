These are things that are planned added 'some time in the future'.
Please try Mumble out before you comment on any of the ideas below.

If you want to help out with any of the below, **great\!** Be aware that
the mumble code is changing all the time, so please drop by the forums
and let us know if you want to work on something so we avoid duplicate
efforts.

**Note: This list is not meant to be a point by point representations of
tasks to be done for a specific release but is merely a reminder for the
developers. New items might be added or existing ones moved and removed
anytime during development.**

## TODO for 1.X.X

  - Add session awareness
  - Group flags
  - Put Qt 4.5 translation comments in more places, to show context of
    translation message.
  - Improve usability a lot (e.g Restructure options menu)
  - Overlay configuration preview (maybe + on-desktop overlay)
  - Overlay for DirectX 9ex, 11

## TODO for statistics

  - Migrate to PDO
  - Add murmur stats
  - Add caching
  - Look for fancy pie-like stuff like jgraph, open-flash-chart2, etc

## Future

### Video

The current overlay texture system is designed for high speed texture
transfers in a format that happens to be 60 pixels high. This is no
coincidence.

Using H.264 encoding, 80x60 pixels is small enough that we can encode a
15fps video stream with minimal CPU impact. The bitrate will also be low
(lower than existing audio streams), and with a bit of filtering the
quality is near perfect. I really mean this; what filtering did for the
audio quality in Mumble it also does for video quality.

I'd like to see this happen; I miss seeing my friends when we're gaming.
It's one thing to hear enthusiasm, it's quite another to see it.

There are two major challenges. The first is a technical one. 80x60
pixels is not much. It is enough to see a face clearly, if the face is
the only thing in the picture. However, most people have their cameras
placed so that 70% of the picture area is the room they are sitting in.
That will not give a good enouh picture. So, we'll need a method to
extract what we need from the image.

The second is bandwidth. Yes, the video stream will use less bandwidth
that an audio stream, but it will be going the whole time. This means
that while audio bandwidth scales linearly with the number of users,
video bandwidth scales exponentially. For example, if we assume that
each user has 30 kbit/s of audio and 20 kbit/s of video. When one user
talks, the others shut up. With 10 users, that's 9\*30=270 kbit/s out
from the server. Video, which is going the entire time, is
9\*20=180kbit/s *for each user*, giving us a total of 1.8Mbit/s. For all
clans and guilds who host their servers somewhere with free bandwidth,
this is not a problem. However, I don't really want to know what a
2mbit/s commercial hosting is going to cost. I doubt it's cheap.

Some suggestions have been brought up by the community:

  - Using WebM instead of H.264. When the time comes, we will look into
    it. VP8/WebM has the advantage of better licensing. H.264 with its
    free encoder x264 has the advantage of longer history and (thus)
    performance. We are aware WebM is improving in the performance field
    as well
    though.<sup>[1](https://sourceforge.net/tracker/index.php?func=detail&aid=3563031&group_id=147372&atid=768008)</sup>
  - Instead of continuous transmission, only transmit video when the
    user talks – as an optional
    feature.<sup>[1](https://sourceforge.net/tracker/index.php?func=detail&aid=3563954&group_id=147372&atid=768008)</sup>

[Category:Documentation
English](Category:Documentation_English "wikilink")
[Category:Development](Category:Development "wikilink")