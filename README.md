# GStreamer Plugins Collection

This repository contains GStreamer plugins as submodules.

## Available Plugins

| Plugin | Description | Repository |
|--------|-------------|------------|
| gstdtmfpinsrc | DTMF PIN Detection Plugin | [gstdtmfpinsrc](https://github.com/TVforME/gstdtmfpinsrc) |
| gsttbs6324src | TBS6324 Source Plugin | [gsttbs6324src](https://github.com/TVforME/gsttbs6324src) |
| gstmorsesrc | Morse Code Source Plugin | [gstmorsesrc](https://github.com/TVforME/gstmorsesrc) |

## Quick Start

### Clone with Submodules
```bash
git clone --recurse-submodules https://github.com/TVforME/gstreamer.git
cd gstreamer
```

### Update All Submodules
```bash
git submodule update --remote --merge
```

### Build Individual Plugin
```bash
cd gstdtmfpinsrc  # or gsttbs6324src or gstmorsesrc
make clean && make
sudo make install
```

## Plugin Documentation

### gstdtmfpinsrc - DTMF PIN Detection
Detects DTMF PIN codes from audio streams and emits bus messages.

**Configuration**: Edit `codes.pin` to define your PIN codes.

**Usage Example**:
```bash
gst-launch-1.0 filesrc location=audio.wav ! \
  decodebin ! audioconvert ! audioresample ! audio/x-raw,rate=8000 ! \
  dtmfpinsrc config-file=codes.pin pass-through=true ! \
  audioconvert ! autoaudiosink
```

### gsttbs6324src - TBS6324 Source
GStreamer source element for TBS6324 DVB tuner card.

### gstmorsesrc - Morse Code Source
Generates Morse code audio signals.

## Adding New Submodules

To add a new plugin as a submodule:
```bash
git submodule add https://github.com/TVforME/your-plugin.git
git add .gitmodules
git commit -m "Add new plugin submodule"
git push
```

## Author

TVforME

## License

See individual plugin repositories for license information.
