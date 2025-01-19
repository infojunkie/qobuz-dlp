# qobuz-dlp
Search, explore and download Lossless and Hi-Res music from [Qobuz](https://www.qobuz.com/).

This is a fork of the [original repo which has gone unmaintained](https://github.com/vitiko98/qobuz-dl).

[![PyPI Version](https://img.shields.io/pypi/v/qobuz-dlp.svg)](https://pypi.org/project/qobuz-dlp/)

## Features

* Download FLAC and MP3 files from Qobuz
* Explore and download music directly from your terminal with **interactive** or **lucky** mode
* Download albums, tracks, artists, playlists and labels with **download** mode
* Download music from last.fm playlists (Spotify, Apple Music and Youtube playlists are also supported through this method)
* Queue support on **interactive** mode
* Effective duplicate handling with own portable database
* Support for albums with multiple discs
* Support for M3U playlists
* Downloads URLs from text file
* Extended tags
* And more

## Getting started

#### Get an active subscription to Qobuz

#### Install qobuz-dlp with pip
##### Linux / MAC OS
```
pip3 install --upgrade qobuz-dlp
```
##### Windows
```
pip3 install windows-curses
pip3 install --upgrade qobuz-dlp
```
#### Run qobuz-dlp and enter your credentials
##### Linux / MAC OS
```
qobuz-dlp
```
##### Windows
```
qobuz-dlp.exe
```

> If something fails, run `qobuz-dlp -r` to reset your config file.

## Examples

### Download mode
Download URL in 24B<96khz quality
```
qobuz-dlp dl https://play.qobuz.com/album/qxjbxh1dc3xyb -q 7
```
Download multiple URLs to custom directory
```
qobuz-dlp dl https://play.qobuz.com/artist/2038380 https://play.qobuz.com/album/ip8qjy1m6dakc -d "Some pop from 2020"
```
Download multiple URLs from text file
```
qobuz-dlp dl this_txt_file_has_urls.txt
```
Download albums from a label and also embed cover art images into the downloaded files
```
qobuz-dlp dl https://play.qobuz.com/label/7526 --embed-art
```
Download a Qobuz playlist in maximum quality
```
qobuz-dlp dl https://play.qobuz.com/playlist/5388296 -q 27
```
Download all the music from an artist except singles, EPs and VA releases
```
qobuz-dlp dl https://play.qobuz.com/artist/2528676 --albums-only
```

#### Last.fm playlists
> Last.fm has a new feature for creating playlists: you can create your own based on the music you listen to or you can import one from popular streaming services like Spotify, Apple Music and Youtube. Visit: `https://www.last.fm/user/<your profile>/playlists` (e.g. https://www.last.fm/user/vitiko98/playlists) to get started.

Download a last.fm playlist in the maximum quality
```
qobuz-dlp dl https://www.last.fm/user/vitiko98/playlists/11887574 -q 27
```

Run `qobuz-dlp dl --help` for more info.

### Interactive mode
Run interactive mode with a limit of 10 results
```
qobuz-dlp fun -l 10
```
Type your search query
```
Logging...
Logged: OK
Membership: Studio


Enter your search: [Ctrl + c to quit]
- fka twigs magdalene
```
`qobuz-dlp` will bring up a nice list of releases. Now choose whatever releases you want to download (everything else is interactive).

Run `qobuz-dlp fun --help` for more info.

### Lucky mode
Download the first album result
```
qobuz-dlp lucky playboi carti die lit
```
Download the first 5 artist results
```
qobuz-dlp lucky joy division -n 5 --type artist
```
Download the first 3 track results in 320 quality
```
qobuz-dlp lucky eric dolphy remastered --type track -n 3 -q 5
```
Download the first track result without cover art
```
qobuz-dlp lucky jay z story of oj --type track --no-cover
```

Run `qobuz-dlp lucky --help` for more info.

### Other
Reset your config file
```
qobuz-dlp -r
```

By default, `qobuz-dlp` will skip already downloaded items by ID with the message `This release ID ({item_id}) was already downloaded`. To avoid this check, add the flag `--no-db` at the end of a command. In extreme cases (e.g. lost collection), you can run `qobuz-dlp -p` to completely reset the database.

## Usage
```
usage: qobuz-dlp [-h] [-r] {fun,dl,lucky} ...

The ultimate Qobuz music downloader.
See usage examples on https://github.com/vitiko98/qobuz-dl

optional arguments:
  -h, --help      show this help message and exit
  -r, --reset     create/reset config file
  -p, --purge     purge/delete downloaded-IDs database

commands:
  run qobuz-dlp <command> --help for more info
  (e.g. qobuz-dlp fun --help)

  {fun,dl,lucky}
    fun           interactive mode
    dl            input mode
    lucky         lucky mode
```

## Module usage
Using `qobuz-dlp` as a module is really easy. Basically, the only thing you need is `QobuzDL` from `core`.

```python
import logging
from qobuz_dl.core import QobuzDL

logging.basicConfig(level=logging.INFO)

email = "your@email.com"
password = "your_password"

qobuz = QobuzDL()
qobuz.get_tokens() # get 'app_id' and 'secrets' attrs
qobuz.initialize_client(email, password, qobuz.app_id, qobuz.secrets)

qobuz.handle_url("https://play.qobuz.com/album/va4j3hdlwaubc")
```

Attributes, methods and parameters have been named as self-explanatory as possible.

## A note about Qo-DL
- `qobuz-dlp` is a continuation of the work started by `qobuz-dlp`, written by vitiko98.
- `qobuz-dl` is inspired in the discontinued Qo-DL-Reborn. This tool uses two modules from Qo-DL: `qopy` and `spoofer`, both written by Sorrow446 and DashLt.

## Disclaimer
* This tool was written for educational purposes. I will not be responsible if you use this program in bad faith. By using it, you are accepting the [Qobuz API Terms of Use](https://static.qobuz.com/apps/api/QobuzAPI-TermsofUse.pdf).
* `qobuz-dlp` is not affiliated with Qobuz
