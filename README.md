# Plexmatch

[![English](https://img.shields.io/badge/docs-English-blue)](./README.md) [![简体中文](https://img.shields.io/badge/docs-简体中文-yellow)](./docs/README.zh-CN.md)

A Python tool for generating `.plexmatch` files for Plex Media Server to help correctly match video files with complex filenames.

## Features

- Automatically scan video files in specified directory
- Support multiple video formats (mp4, mkv, avi, mov, etc.)
- Extract episode numbers from filenames
- Generate Plex-compatible `.plexmatch` files
- Support ordered matching mode
- Support custom season number setting

## Requirements

No external dependencies required. Uses Python standard library only.

## Usage

### Basic Usage

```bash
python -m Plexmatch -d "C:\your\video\directory"
```

### Network Path

```bash
python -m Plexmatch -d "//Network\directory"
```

### Command Line Arguments

- `-d, --directory`: Specify video file directory (required)
- `-o, --order`: Select only ordered files
- `-ow, --overwrite`: Overwrite existing .plexmatch file
- `-s, --season`: Specify season number

### Examples

```bash
# Basic scan
python -m Plexmatch -d "C:\TV Shows\My Series\Season 1"

# Ordered matching with custom season
python -m Plexmatch -d "C:\TV Shows\My Series\Season 2" -o -s 2

# Overwrite existing file
python -m Plexmatch -d "C:\TV Shows\My Series\Season 1" -ow
```

## Supported Video Formats

3g2, 3gp, asf, asx, avc, avi, avs, bivx, bup, divx, dv, dvr-ms, evo, fli, flv, m2t, m2ts, m2v, m4v, mkv, mov, mp4, mpeg, mpg, mts, nsv, nuv, ogm, ogv, tp, pva, qt, rm, rmvb, sdp, svq3, strm, ts, ty, vdr, viv, vob, vp3, wmv, wtv, xsp, xvid, webm

## How It Works

1. Scan all video files in the specified directory
2. Filter out special files (like [SP], [MENU], etc.)
3. Sort files using natural sorting
4. Extract episode numbers from filenames
5. Generate .plexmatch file with format `ep: S{season}E{episode}: {filename}`

## Notes

- If `.plexmatch` file already exists in the directory, the program will exit (unless using `-ow` parameter)
- The program automatically skips files containing `[SP]` and `[MENU]` markers
- Episode numbers are extracted from filenames using regex (looking for 2-3 digit numbers)

## License

See LICENSE file for details.
