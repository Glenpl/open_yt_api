# open-yt-api
[![Code Health](https://landscape.io/github/Glenpl/open-yt-api/master/landscape.svg?style=flat)](https://landscape.io/github/Glenpl/open-yt-api/master)
[![Build Status](https://travis-ci.org/Glenpl/open-yt-api.svg?branch=master)](https://travis-ci.org/Glenpl/open-yt-api)
[![Coverage Status](https://coveralls.io/repos/github/Glenpl/open-yt-api/badge.svg?branch=master)](https://coveralls.io/github/Glenpl/open-yt-api?branch=master)

This is an open YouTube API library.
It might be slow because it scrapes and parses actual YouTube HTMLs.

The library is still under development and there may be significant differences between versions.

Installation
--------------------
```bash
pip install openytapi
```

Usage example
--------------------
```python
from youtube.api import YoutubeApi

found_items = YoutubeApi().search('lana del rey')
found_playlists = YoutubeApi().search_playlists('lana del rey')

print(found_items)
```

Documentation
--------------------
The main API class is YoutubeApi, which consists of 7 methods:
```
constructor(http_fetcher=None)

search(search_string: str) -> List of VideoSignature, ChannelSignature and PlaylistSignature
search_videos(search_string: str) -> List of VideoSignature
search_channels(search_string: str) -> List of ChannelSignature
search_playlists(search_string: str) -> List of PlaylistSignature
get_video(video_id: str) -> YoutubeVideo object
get_playlist(playlist_id: str) -> YoutubeChannel object
get_channel(channel_id: str) -> YoutubePlaylist object
```
YoutubeApi constructor takes an optional http_fetcher argument.
Object passed as http_fetcher is used to fetch www page source - it has to implement such an interface:
```python
class Fetcher():
    def __init__(): pass  # default constructor
    def fetch_page(url): pass  # returns utf-8 decoded page source
```
It's probably best to just let the YoutubeApi use it's default http_fetcher - the one that works just fine.

---

#####VideoSignature
It's a value object. 
```
get_url() -> str
get_id() -> str
get_length() -> str
get_title() -> str
get_author() -> str
get_views() -> str
get_thumbnail_url() -> str
```
---

#####ChannelSignature
It's a value object. 
```
get_url() -> str
get_id() -> str
get_name() -> str
get_videos_amount() -> str
get_subscriptions() -> str
get_thumbnail_url() -> str
```
---

#####PlaylistSignature
It's a value object. 
```
get_url() -> str
get_id() -> str
get_name() -> str
get_length() -> str
get_thumbnail_url() -> str
get_author() -> str
get_first_video_id() -> str
get_first_video_url() -> str
```

License
--------------------
MIT license.
