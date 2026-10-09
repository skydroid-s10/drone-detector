# DeviceHelper

The project maintainer supplied `S10升级助手(2).zip` for static analysis. The original archive and its bundled vendor binaries are not included in this public repository; do not upload them until redistribution rights are clear.

## Initial inventory

- Archive size: 23,528,459 bytes
- Archive SHA-256: `cbc0d15de36167cadc84d6288be7b58416762b791f9bd799d0756656b2c2a8c3`
- ZIP integrity check: passed
- Entries: 57, including directories
- Main executable: `S10_Dev.exe`, 84,992 bytes
- Executable SHA-256: `90699f7403973fe57b79054007d906aa61fedc80c0dd8e7c27696f3f8dbc937c`
- Executable format: 32-bit x86 Windows PE
- Runtime: Qt 5; package includes Qt Serial Port and Qt Network libraries
- No obvious firmware image or separate driver installer was present in the ZIP member list.

Static strings/imports indicate serial-port enumeration/configuration/read-write paths, a local `*.bin` file picker, a `./Setting.ini` settings path, firmware/version labels, and an embedded update-metadata URL. These are preliminary observations, not a decoded protocol or proof of supported models.

## Research notes

- [ZIP inventory and provenance](../../documentation/devicehelper/overview.md)
- [Application static analysis](../../documentation/devicehelper/application-analysis.md)
- [Serial/update protocol checklist](../../documentation/devicehelper/protocol-research.md)

Do not assume the updater is universal across S10-family devices without evidence. Do not run unknown executables as part of static analysis, flash reconstructed firmware, or publish vendor binaries without permission. Real update protocol claims require a documented successful vendor update and verified device/image compatibility.
