# DeviceHelper serial/update protocol research checklist

## Current evidence

Static inspection of `S10_Dev.exe` shows Qt Serial Port API references, read/write-related symbols, firmware-update labels, a local `*.bin` file filter, and an embedded update-metadata URL. This is evidence of relevant code paths, not a decoded protocol.

The supplied ZIP contains 57 entries and no obvious firmware image or separate driver installer in its member list. The updater's exact behavior remains to be established.

## Evidence to collect before designing a replacement flasher

### 1. Device and environment

- Exact device model and hardware revision.
- Firmware version before and after the official update.
- Windows version, USB cable, USB port, and driver state.
- Exact updater archive and executable hashes.
- Whether the device enters a documented upgrade/boot mode.

### 2. Serial transport

Record from static code analysis and, if authorized, a successful update capture:

- Port enumeration and device-selection logic.
- Baud rate, data bits, parity, stop bits, and flow control.
- Open/close sequence and timeouts.
- Whether the application uses a USB serial bridge or another driver interface.

Do not guess settings based on unrelated Skydroid products.

### 3. Message-level protocol

For each observed message, record:

- Direction (host-to-device or device-to-host).
- Timestamp and byte count.
- Raw bytes in hex, with sensitive identifiers removed.
- Candidate framing/header, length fields, command, address/offset, payload, and trailer.
- Response/ACK/NAK and timeout behavior.
- Retry count and whether retries repeat the same payload.
- Integrity mechanism (CRC/checksum/hash) and how it is calculated.
- Finalization, verification, and reboot sequence.

Keep raw captures separate from decoded interpretations. Mark each field as observed, hypothesized, or verified.

### 4. Firmware and compatibility

- Hash the exact local firmware file before testing.
- Record its origin, filename, claimed version, size, and target model.
- Compare the updater's displayed model/version information with the file metadata and device result.
- Do not infer S10/S10G2 family compatibility from a shared application or a selectable model label.
- Do not test reconstructed or modified firmware until compatibility, integrity, and recovery have been established.

## Acceptance criteria for an independent updater

A replacement tool should not be considered safe until it can, at minimum:

1. Identify the connected device unambiguously.
2. Reject an unknown or mismatched model/image.
3. Verify the exact image hash and expected format.
4. Reproduce the vendor transport and protocol without omitting validation.
5. Handle timeout, disconnect, NAK, and retry cases safely.
6. Verify the device's post-update version and report failure honestly.
7. Be tested against a known-good baseline with a documented recovery procedure.

Until these criteria are met, use the vendor updater for real firmware updates and treat protocol work as research only.
