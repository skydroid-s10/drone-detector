# DeviceHelper ZIP: initial inventory

## Artifact identity

- Supplied archive: `S10升级助手(2).zip`
- Archive size: 23,528,459 bytes
- SHA-256: `cbc0d15de36167cadc84d6288be7b58416762b791f9bd799d0756656b2c2a8c3`
- ZIP integrity test: passed using Python's ZIP reader; no corrupt member was reported.
- Archive entries: 57, including directory entries.
- Inspection date: 2026-10-09
- Scope: static inventory and executable metadata only. The executable was not launched.

The archive name and supplied context associate this with the Skydroid S10 DeviceHelper/update assistant. This inventory does not independently prove vendor authenticity, signature status, or compatibility with every S10-family model.

## Observed package layout

The archive contains one top-level directory, `S10升级助手/`, with:

- `S10_Dev.exe` — Windows PE executable, 84,992 bytes.
- Qt 5 runtime libraries: `Qt5Core.dll`, `Qt5Gui.dll`, `Qt5Network.dll`, `Qt5SerialPort.dll`, `Qt5Svg.dll`, `Qt5Widgets.dll`.
- Qt platform/image plugins, translation resources, and supporting runtime DLLs.
- No obvious firmware image with a `.bin`, `.hex`, or similarly named firmware extension appeared in the ZIP member list.
- No separate driver folder or driver installer appeared in the ZIP member list.

The absence of an obvious firmware image in this archive does not rule out downloading firmware at runtime, loading a local file selected by the user, or storing files elsewhere.

## Executable metadata

- File: `S10_Dev.exe`
- Size: 84,992 bytes
- SHA-256: `90699f7403973fe57b79054007d906aa61fedc80c0dd8e7c27696f3f8dbc937c`
- PE machine: `0x014c` (32-bit x86)
- Optional-header magic: `0x010b` (PE32)
- Sections observed: `.text`, `.data`, `.rdata`, `.eh_fram`, `.bss`, `.idata`, `.CRT`, `.tls`.

## High-confidence observations from static strings/imports

The executable contains strings/symbols indicating use of:

- Qt Serial Port APIs, including port enumeration, port naming, opening/closing a port, baud-rate/data-bit/stop-bit/parity configuration, and read/write operations.
- A settings path named `./Setting.ini`.
- A local firmware file picker filter: `Model File(*.bin)`.
- Firmware/version-related labels such as `versionName`, `versionCode`, and `versionol`.
- An online metadata URL embedded in the executable: `http://www.skydroid.xin/download/app/app-Remote-control-mcu-update.json`.
- A log/string path including `doProcessReadyRead`, plus `initFirmwareInfo` and `upgrade` identifiers.

These strings support the conclusion that this is a Qt-based Windows application with serial-port and firmware-update related code. Strings alone do not establish the exact packet format, serial settings used during an update, firmware authenticity checks, or whether every model is supported.

## Safety and redistribution

- Preserve the supplied ZIP unchanged and keep its SHA-256 with the research notes.
- Do not commit the vendor executable, Qt DLLs, or other bundled binaries to this public repository unless redistribution permission is confirmed.
- Publish independently written analysis, hashes, metadata, and original documentation instead.
- Do not run the updater against hardware as part of static analysis. Any future live test should use the exact model, known-good firmware, stable power, and a recovery plan.

## Next work

1. Inspect `Setting.ini` handling and any generated settings without running the program.
2. Recover readable UI strings and Qt metadata more comprehensively.
3. Disassemble the executable and trace serial-port configuration and read/write call sites.
4. Establish whether the HTTP metadata endpoint is still live and document the schema only if it can be checked safely.
5. Capture a successful official update before making claims about protocol framing, acknowledgements, checksums, or bootloader behavior.
