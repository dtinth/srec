# srec

This is a simple web-based screen recording application that allows users to capture their screen, optionally add microphone audio, and save the recording to a selected directory.

## Features

- Screen sharing with audio capture
- Optional microphone audio input
- Customizable recording directory
- Real-time recording information (file size and latest recorded file)
- Experimental WebSocket streaming support

## Technical Details

- The application uses the `MediaDevices` API to capture screen and audio.
- Recordings are saved in the MKV format with H.264 video codec (Chrome, Edge) or WebM format with VP8 video codec (Firefox).
- The File System Access API is used to allow users to select a save directory and write files directly to the file system.
- Alternatively stream the recording to a WebSocket server (experimental).

## Browser Support

From my testing,

- **Google Chrome** as of v127
  - Can record at high framerate (60 fps).
  - Can record as H.264 MKV file, which can be easily remuxed to MP4.
  - However, retina displays are recorded at half resolution.
  - Can record directly to a file system.
- **Firefox** as of v129
  - Can record at high resolution (e.g. retina display at full resolution).
  - Can record as VP8 WebM file.
  - However, the framerate seems to be lower than Chrome. The output file was a variable framerate file.
  - Does not support File System Access API. To work around that, an [experimental WebSocket streaming feature](#experimental-websocket-streaming) is available.

## Experimental WebSocket Streaming

1. Hold the Alt/Option key while clicking "Select Recording Directory".
2. Enter a WebSocket URL (ws://) to stream the recording to.
3. Proceed with recording as normal.

For an example WebSocket server implementation, see [srec-server](https://github.com/dtinth/srec-server).
