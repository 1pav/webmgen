# README

This script converts the given input file to webm. It's a wrapper around ffmpeg with the purpose of being easier to use when doing simple conversions. Files are encoded with VP8/Vorbis.

## Features

- Downscale resolution
- Set video and audio bitrate
- Limit output size
- Split output into multiple files of given size
- Cut video before encoding

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
                    than requested size. If -p is not set, bitrate specified by -v is ignored.
  -p                split output into multiple files. Requires -s.
  -c [START],[END]  cut input file from START to END before encoding.
                    START, END are formatted as HH:MM:SS; only one can be omitted.
  -d DIRECTORY      output DIRECTORY (default: directory of input FILE)
  -t THREADS        number of threads to use for encoding (default: one less than the number of CPUs)
  -h                show help and exit
```