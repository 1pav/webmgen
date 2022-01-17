# README

This script converts the given input file to webm. It's a wrapper around ffmpeg with the purpose of being easier to use when doing simple conversions. Files are encoded with VP8/Vorbis.

## Features

- Set video and audio bitrate
- Downscale resolution
- Limit output size
- Split output into multiple files of given size
- Cut video before encoding

## Examples

Convert to webm using default encoding settings (`-v 1M`, `-a 128K`):

```
webmgen input.mp4
```

Set video and audio bitrate to 2 Mb/s and 256 Kb/s respectively:

```
webmgen -v 2M -a 256K input.mp4
```

Limit file size to 5 MB:

```
webmgen -s 5M input.mp4
```

Cut first 30 seconds of video before converting:

```
webmgen -c ,00:00:30 input.mp4
```

Split into multiple files of size 500 KB:

```
webmgen -p -s 500K input.mp4
```

Downscale resolution to 720p, keeping aspect ratio:

```
webmgen -r 720 input.mp4
```

## Usage

```
Usage: webmgen [OPTIONS] FILE
Convert FILE to VP8-encoded webm.
Output is saved in the same directory of FILE, unless -d option is used.
Where appropriate, options accept the following unit prefixes: K, M, G.

Options:
  -r RESOLUTION     vertical RESOLUTION (keeps aspect ratio)
  -v BITRATE        video BITRATE (default: 1M)
  -a BITRATE        audio BITRATE (default: 128K)
  -s SIZE           SIZE of output file(s), expressed in bytes. Actual size can be slightly more
                    or less than requested size. If -p is not set, bitrate specified by -v is ignored.
  -p                split output into multiple files. Requires -s.
  -c [START],[END]  cut input file from START to END before encoding.
                    START, END are formatted as HH:MM:SS; only one can be omitted.
  -d DIRECTORY      output DIRECTORY (default: directory of input FILE)
  -t THREADS        number of threads to use for encoding (default: one less than the number of CPUs)
  -h                show help and exit
```