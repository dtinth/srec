# srec

This is a simple web-based screen recording application that allows users to capture their screen, optionally add microphone audio, and save the recording to a selected directory.

## Features

- Screen sharing with audio capture
- Optional microphone audio input
- Customizable recording directory
- Real-time recording information (file size and latest recorded file)

## Technical Details

- The application uses the `MediaDevices` API to capture screen and audio.
- Recordings are saved in the MKV format with H.264 video codec.
- The File System Access API is used to allow users to select a save directory and write files directly to the file system.
