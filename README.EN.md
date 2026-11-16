# QMK / VIA JSON Archive

[한국어](README.MD) | **English**

A community archive that collects and preserves QMK- and VIA-related JSON files for keyboards and PCBs.

This repository brings together resources scattered across manufacturer websites, product pages, and Discord, helping people keep using their keyboards even after the original distribution channels disappear.

## Purpose

- **Long-term preservation**: Protect files from being lost when websites shut down, domains expire, Discord servers or channels are deleted, or attachment links expire.
- **Easier access**: Reduce the need to track down separate download pages or join multiple Discord servers.
- **Continued use of older hardware**: Help owners configure and maintain discontinued keyboards and PCBs that no longer receive support.
- **Version and variant preservation**: Keep resources for different PCB revisions, connection modes, and hot-swap or solder variants distinguishable, and retain access to earlier files.
- **Source and compatibility information**: Record where files came from and which hardware they target to help users choose the correct file.
- **Shared community knowledge**: Share privately preserved files and practical findings to reduce repeated searches and file requests.

This is an independent archive. A file's inclusion does not mean that the keyboard is officially supported by QMK or VIA, or that the file has been tested on every hardware variant.

## File Types and Terminology

`.json` is a file format, and JSON files are not interchangeable. Check the file contents and the original distribution instructions rather than relying on the filename alone.

| Name | Purpose | Where to use it |
| --- | --- | --- |
| **VIA Keyboard Definition** | Defines keyboard identification, the matrix, physical layout, layout options, and supported configuration UI. | Load it in VIA's `Design` tab. |
| **QMK Keymap JSON** | Describes a keymap, including the QMK keyboard identifier, layout macro, and keycodes for each layer. | Use it with QMK Configurator or QMK CLI. |
| **Layout JSON saved from VIA** | Stores user settings exported from VIA, such as key assignments. | Save or restore it using VIA's `Save Current Layout` / `Load Saved Layout` features. |
| **QMK `info.json` / `keyboard.json`** | Provides data-driven configuration for keyboard hardware, layouts, and other QMK Firmware settings. | Use it in the QMK source and build environment; distinguish it from a VIA Keyboard Definition. |

This table explains the different JSON file types. It does not mean that every type is available for every model in this repository.

> A VIA Keyboard Definition is not firmware. Loading a JSON file does not add VIA support to a keyboard or update its firmware. Also, `layouts.keymap` in a VIA Keyboard Definition describes physical key positions and matrix coordinates; it serves a different purpose from the keycode assignments stored in `layers` in a QMK Keymap JSON file.

## Folder Structure

Files are generally organized as **manufacturer or brand → keyboard or PCB model → related files**. Some models may have additional subfolders for versions or PCB variants.

| Path or pattern | Description |
| --- | --- |
| `<manufacturer or brand>/` | Top-level manufacturer or brand folder, such as `Geonworks/`, `QwertyKeys/`, or `TKD/`. |
| `<manufacturer or brand>/[manufacturer or brand] <model>/` | Resources for a specific keyboard or PCB. |
| `ETC/` | Miscellaneous resources. |
| `README.MD` | Korean overview, file types, usage instructions, and contribution guidelines. |
| `README.EN.md` | English version of the README. |

Examples of paths in the repository:

| Example path | Description |
| --- | --- |
| `Alexotos/[Alexotos] Manta65/` | Resources for the Alexotos Manta65 |
| `Cidoo/[Cidoo] ABM066/` | Resources for the Cidoo ABM066 |
| `GDK Lab/[GDK Lab] KV1-65/kv1-65_hotswap_wired.json` | VIA Keyboard Definition for the wired, hot-swap KV1-65 |
| `TKD/[TKD] Pt.1-75/TKD - Pt.1-75 Solderable.json` | VIA Keyboard Definition for the solder PCB version of the Pt.1-75 |

GitHub may display intermediate folders as a single combined path, but the manufacturer and model folders remain separate directories. Check existing categories and filenames before adding resources.

## Requirements

### General Checks

- Identify the **actual PCB model and revision installed in your keyboard**, not just the keyboard model. The same case may house different PCBs.
- Choose the correct variant as distinguished by the original distributor, such as hot-swap or solder, ANSI or ISO, and wired or wireless.
- Check the source, target firmware, and version notes where available. The newest file may not support every older PCB.

### Using a VIA Keyboard Definition

- Your keyboard must have **VIA-compatible firmware** installed. Running QMK Firmware alone does not necessarily mean that VIA is enabled.
- The [VIA web app](https://usevia.app/) requires a browser with WebHID support and permission to access the device. Chrome or Edge can be used on supported platforms.
- Use a connection mode supported by the firmware. Whether VIA configuration works over Bluetooth or 2.4 GHz depends on the model; follow the manufacturer's instructions.
- The definition's USB Vendor ID (`vendorId`), Product ID (`productId`), matrix, and layout must match the target firmware. Matching VID/PID alone does not guarantee full compatibility.
- Select a V2 or V3 definition according to the target firmware and the original instructions. The definition version and the VIA Firmware Protocol version are distinct.

### Using a QMK Keymap JSON File

- Prepare [QMK Configurator](https://config.qmk.fm/), or QMK CLI with the required build environment.
- Your QMK version must support the `keyboard`, `layout`, and keycodes specified in the JSON file.
- Manufacturer-specific keyboards or forks that QMK Configurator does not support may require the source and build environment provided by the manufacturer.

A QMK build environment is not required simply to download and preserve files.

## Usage

### 1. Find and Download a File

1. Find your keyboard or PCB model in the manufacturer or brand folder. You can also search using GitHub's `Go to file` feature.
2. Select the file matching your PCB variant, revision, connection mode, and version.
3. Use `Download raw file` on the file page. Make sure you download the actual file rather than saving the webpage as HTML.

To keep a copy of the entire archive, use `Code` → `Download ZIP` or clone the repository:

```sh
git clone https://github.com/KBD-Type-S/via_json.git
```

### 2. Load a VIA Keyboard Definition

If VIA already recognizes your keyboard correctly, you may not need to load a definition manually.

1. Open [VIA](https://usevia.app/) and connect your keyboard as instructed by the manufacturer.
2. In `Settings`, enable `Show Design tab`.
3. In the `Design` tab, use `Load` under `Load Draft Definition` to select the appropriate VIA Keyboard Definition.
4. If you are using a V2 definition and your app provides a `Use V2 definitions` option, set it according to the original instructions.
5. Connect and authorize the device in the `Configure` tab, then check that the displayed layout and layout options match your keyboard.
6. To preserve your existing settings, back them up with `Save Current Layout` before making changes.

Menu names and locations may vary by app version and display language. Do not load a QMK Keymap JSON file or a Layout JSON exported from VIA through `Load Draft Definition`.

### 3. Use a QMK Keymap JSON File

Import the file into QMK Configurator, or build it using QMK CLI as shown below. Replace `path/to/keymap.json` with the actual file path.

```sh
qmk compile path/to/keymap.json
```

To flash the resulting firmware, follow the procedure appropriate for your PCB's MCU and bootloader. Downloading a file from this repository does not, by itself, mean that flashing is necessary.

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| The device does not appear in VIA | Check for VIA-compatible firmware, a data-capable cable, the correct connection mode, browser WebHID support, and device permissions. Linux may require udev configuration for device access. |
| The device is not recognized after loading a definition | Check the PCB revision, VID/PID, and compatibility between the V2 or V3 definition and the firmware. |
| An error occurs when loading JSON | Check that you downloaded JSON rather than HTML, selected the correct JSON file type, and are using an app that supports the format. |
| The layout or key positions are incorrect | Check for a definition intended for a different PCB, a different hot-swap or solder variant, or incorrect layout options. |
| RGB lighting or encoders do not work as expected | Check that the firmware implements the features exposed by the definition and that the definition matches the firmware. |

Before changing VID/PID or matrix values to make an unrecognized device connect, verify that you have the correct resources for the PCB and firmware.

## Contributing

Report missing files, new versions, source information, misclassified resources, or compatibility issues through an [Issue](https://github.com/KBD-Type-S/via_json/issues) or [Pull Request](https://github.com/KBD-Type-S/via_json/pulls).

### Recommendations for Adding Files

- Check whether the manufacturer and model folders already exist.
- Preserve original filenames and contents where possible. When differentiation is necessary, clearly identify the PCB variant, revision, or version in the filename or a subfolder.
- Before overwriting an older file with a newer version, check whether the older version is still needed for an older PCB or firmware.
- Keep modified files distinguishable from the originals, and document what changed and why.
- Record JSON syntax validation separately from testing on physical hardware. Valid JSON does not establish hardware compatibility.
- Check redistribution conditions and avoid including personal information or content that is restricted from public distribution.

Include the following information in the PR description or a README in the model folder to help others select the correct file. Mark unknown information as `Unconfirmed` rather than guessing.

| Field | Information to record |
| --- | --- |
| Manufacturer and model | Keyboard model and PCB model |
| Hardware variant | PCB revision, hot-swap or solder, connection mode, etc. |
| File type | VIA Keyboard Definition, QMK Keymap JSON, etc. |
| Source | Original URL, manufacturer download page, or Discord message link |
| Preservation details | Date obtained, release date, or supplied version |
| Compatibility | Target firmware version, V2 or V3 definition, and any usage requirements |
| Verification status | Untested / JSON syntax validated / tested on a specified PCB and firmware |
| Changes | Whether the file is original or modified, modifications made, and differences from earlier versions |
| Rights | Original license or redistribution conditions |

## Attribution and Rights

Please respect each file's creator, manufacturer, and original distributor. Archived resources remain subject to their original licenses and redistribution conditions. Inclusion in this repository does not automatically grant permission to modify or redistribute them freely.

If attribution needs to be corrected, or a file needs to be modified or removed, open an Issue with the file path and the reason for the request.

## Official Documentation

- [QMK Firmware Documentation](https://docs.qmk.fm/)
- [QMK Configurator: Step by Step](https://docs.qmk.fm/configurator_step_by_step)
- [QMK Keymap JSON Format](https://docs.qmk.fm/configurator_default_keymaps)
- [QMK CLI Commands](https://docs.qmk.fm/cli_commands)
- [VIA Specification — Keyboard Definition](https://www.caniusevia.com/docs/specification/)
- [VIA — Configuring QMK](https://www.caniusevia.com/docs/configuring_qmk/)
- [VIA App Source](https://github.com/the-via/app)
- [Official VIA Keyboard Definitions Repository](https://github.com/the-via/keyboards)
