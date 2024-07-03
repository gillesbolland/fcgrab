# fcgrab

**fcgrab** is a script designed to facilitate the import of DV and HDV video clips captured using `dvgrab` (a utility for capturing raw DV and HDV streams on GNU/Linux) into Final Cut Pro on macOS. It converts a directory of video files into a Final Cut Camera Archive, ensuring compatibility and optimal metadata integration with Final Cut Pro.

## Features

- Converts DV (.dv) and HDV (.m2t) video files into lossless QuickTime (.mov) format suitable for Final Cut Pro.
- Extracts creation dates from original video files and applies them to the transcoded files and its metadata.
- Creates an `FCArchMetadata.plist` file with metadata required for Final Cut Pro projects.
- Uses FFmpeg with `hevc_videotoolbox` codec for fast transcoding optimized for macOS environment.
- Supports maintaining file sizes close to the original (HDV) and similar quality or third of the size for DV files using appropriate bitrates.

## Usage

### Requirements

- FFmpeg installed with `hevc_videotoolbox` support.
- mediainfo command-line tool for extracting creation dates from video files.

### Installation

No installation is required other than ensuring FFmpeg and mediainfo are correctly set up on your macOS system.

### Usage Example

    ```bash
    # Convert a directory of DV and HDV files into a Final Cut Camera Archive
    ./fcgrab /path/to/video/files "Sony HVR-V1E"

### Options

<directory>: Path to the directory containing DV (.dv) or HDV (.m2t) video files captured using dvgrab.
<camera model> (optional): Name of the camera model used for capturing the video. Defaults to "HDV-VCR" or "DV-VCR" depending on the mix of DV and HDV files.

### Notes

This script assumes the original video files were captured using dvgrab from MiniDV camcorders via FireWire (iLink) connection.
The transcoding process ensures compatibility with Final Cut Pro and other Apple solutions by utilizing the hevc_videotoolbox codec and the correct metadata in FFmpeg.
The resulting .mov files are stored in a sub-directory named "Transcoded Media", while the original .dv and .m2t files are moved to "Original Media".
After running the script, you will be prompted whether to keep or delete the original video files.
