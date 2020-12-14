# qobuz-dl
Search, discover and download Lossless and Hi-Res music from [Qobuz](https://www.qobuz.com/).

## Features

* Download FLAC and MP3 files from Qobuz
* Explore and download music directly from your terminal with **interactive** or **lucky** mode
* Download albums, tracks, artists, playlists and labels with **download** mode
* Download music from last.fm playlists (Spotify, Apple Music and Youtube playlists are also supported through this method)
* Queue support on **interactive** mode
* Support for albums with multiple discs
* Downloads URLs from text file
* And more

## Getting started

> You'll need an **active subscription**

#### Install qobuz-dl with pip
##### Linux / MAC OS
```
pip3 install --upgrade qobuz-dl
```
##### Windows
```
pip3 install windows-curses
pip3 install --upgrade qobuz-dl
```
#### Run qobuz-dl and enter your credentials
##### Linux / MAC OS
```
qobuz-dl
```
##### Windows
```
qobuz-dl.exe
```

> If something fails, run `qobuz-dl -r` to reset your config file.

## Examples

### Download mode
Download URL in 24B<96khz quality
```
qobuz-dl dl https://play.qobuz.com/album/qxjbxh1dc3xyb -q 7
```
Download multiple URLs to custom directory
```
qobuz-dl dl https://play.qobuz.com/artist/2038380 https://play.qobuz.com/album/ip8qjy1m6dakc -d "Some pop from 2020"
```
Download multiple URLs from text file
```
qobuz-dl dl this_txt_file_has_urls.txt
```
Download albums from a label and also embed cover art images into the downloaded files
```
qobuz-dl dl https://play.qobuz.com/label/7526 --embed-art
```
Download a Qobuz playlist in maximum quality
```
qobuz-dl dl https://play.qobuz.com/playlist/5388296 -q 27
```
Download all the music from an artist except singles, EPs and VA releases
```
qobuz-dl dl https://play.qobuz.com/artist/2528676 --albums-only
```

#### Last.fm playlists
Last.fm has a new feature for creating playlists: you can create your own based on the music you listen or you can import one from popular streaming services like Spotify, Apple Music and Youtube. Visit: `https://www.last.fm/user/<your profile>/playlists` (e.g. https://www.last.fm/user/vitiko98/playlists) to get started.

Download a last.fm playlist in the maximum quality
```
qobuz-dl dl https://www.last.fm/user/vitiko98/playlists/11887574 -q 27
```

Run `qobuz-dl dl --help` for more info.

### Interactive mode
Run interactive mode with a limit of 10 results
```
qobuz-dl fun -l 10
```
Type your search query
```
Logging...
Logged: OK
Membership: Studio


Enter your search: [Ctrl + c to quit]
- fka twigs magdalene
```
`qobuz-dl` will bring up a nice list of releases. Now choose whatever releases you want to download (everything else is interactive).

Run `qobuz-dl fun --help` for more info.

### Lucky mode
Download the first album result
```
qobuz-dl lucky playboi carti die lit
```
Download the first 5 artist results
```
qobuz-dl lucky joy division -n 5 --type artist
```
Download the first 3 track results in 320 quality
```
qobuz-dl lucky eric dolphy remastered --type track -n 3 -q 5
```

Run `qobuz-dl lucky --help` for more info.

### Other
Reset your config file
```
qobuz-dl -r
```

## Usage
```
usage: qobuz-dl [-h] [-r] {fun,dl,lucky} ...

The ultimate Qobuz music downloader.
See usage examples on https://github.com/vitiko98/qobuz-dl

optional arguments:
  -h, --help      show this help message and exit
  -r, --reset     create/reset config file

commands:
  run qobuz-dl <command> --help for more info
  (e.g. qobuz-dl fun --help)

  {fun,dl,lucky}
    fun           interactive mode
    dl            input mode
    lucky         lucky mode
```

## Module usage 
Using `qobuz-dl` as a module is really easy. Basically, the only thing you need is to initialize `QobuzDL` from `core`.

```python
from qobuz_dl.core import QobuzDL

email = "your@email.com"
password = "your_password"

qobuz = QobuzDL()
qobuz.get_tokens() # get 'app_id' and 'secrets' attrs
qobuz.initialize_client(email, password, qobuz.app_id, qobuz.secrets)

qobuz.handle_url("https://play.qobuz.com/album/va4j3hdlwaubc")
```

Attributes, methods and parameters have been named as self-explanatory as possible.

## A note about Qo-DL
`qobuz-dl` is inspired in the discontinued Qo-DL-Reborn. This program uses two modules from Qo-DL: `qopy` and `spoofer`, both written by Sorrow446 and DashLt.
## Disclaimer
* This tool was written for educational purposes. I will not be responsible if you use this program in bad faith. By using it, you are accepting the [Qobuz API Terms of Use](https://static.qobuz.com/apps/api/QobuzAPI-TermsofUse.pdf).
* `qobuz-dl` is not affiliated with Qobuz
