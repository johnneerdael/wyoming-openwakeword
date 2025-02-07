# Wyoming openWakeWord (Fork)

This project is a fork of [rhasspy/wyoming-openwakeword](https://github.com/rhasspy/wyoming-openwakeword) and is now maintained by [johnneerdael](https://github.com/johnneerdael/wyoming-openwakeword).

This fork was created primarily to replace the `tflite-runtime` dependency with [ai-edge-litert](https://github.com/ai-edge/ai-edge-litert), enabling improved performance on edge devices.

---

## Overview

The Wyoming openWakeWord service implements the [Wyoming protocol](https://github.com/rhasspy/wyoming) as a server for the [openWakeWord](https://github.com/dscripka/openWakeWord) wake word detection system. It offers efficient wake word detection and processing, which can run locally or via a Docker deployment.

---

## Home Assistant Add-on

[![Show add-on](https://my.home-assistant.io/badges/supervisor_addon.svg)](https://my.home-assistant.io/redirect/supervisor_addon/?addon=core_openwakeword)

[Source](https://github.com/home-assistant/addons/tree/master/openwakeword)

---

## Local Install

Clone the repository and set up the Python virtual environment:

```bash
git clone https://github.com/johnneerdael/wyoming-openwakeword.git
cd wyoming-openwakeword
script/setup
```

Run a server that anyone can connect to:

```bash
script/run --uri 'tcp://0.0.0.0:10400' --preload-model ok_nabu
```

See `script/run --help` for additional options, including:

- `--custom-model-dir <DIR>`: Specify a custom directory containing additional wake word models.
- `--debug`: Output detailed debugging information.

**Note:** This fork uses `ai-edge-litert` in place of `tflite-runtime`.

---

## Docker Image

To run the server with Docker:

```bash
docker run -it -p 10400:10400 johnneerdael/wyoming-openwakeword --preload-model 'ok_nabu'
```

### Custom Models

To use custom wake word models with Docker:

```bash
docker run -it -p 10400:10400 -v /path/to/custom/models:/custom johnneerdael/wyoming-openwakeword \
  --preload-model 'ok_nabu' \
  --custom-model-dir /custom
```

[Source](https://github.com/rhasspy/wyoming-addons/tree/master/openwakeword)

---

## Credits

This project is a fork of the original work by the Rhasspy team. Major modifications include replacing `tflite-runtime` with `ai-edge-litert`. For more details on the original implementation, please refer to:

- [rhasspy/wyoming-openwakeword](https://github.com/rhasspy/wyoming-openwakeword)
- [openWakeWord](https://github.com/dscripka/openWakeWord)
