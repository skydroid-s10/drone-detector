# DeviceHelper artifact release note

## Artifact under review

- Supplied archive name: `S10升级助手(2).zip`
- Archive size: 23,528,459 bytes
- Archive SHA-256: `cbc0d15de36167cadc84d6288be7b58416762b791f9bd799d0756656b2c2a8c3`
- Main executable observed inside: `S10_Dev.exe`
- Executable size: 84,992 bytes
- Executable SHA-256: `90699f7403973fe57b79054007d906aa61fedc80c0dd8e7c27696f3f8dbc937c`
- Executable format: Windows PE32, x86
- Runtime indicators: Qt 5, including Qt Serial Port and Qt Network components
- Analysis status: static inspection only; the application was not launched.

These hashes describe the exact supplied files examined in this research session. They do not establish vendor authenticity or that another file with a similar name is identical.

## Public distribution and intended role

The project maintainer reports that DeviceHelper was downloaded from a publicly available Skydroid website download. A publicly accessible copy of the Skydroid S10 user manual describes DeviceHelper as the firmware-upgrade assistant and explains using it to query device/hardware and firmware information and to perform online or local-file updates.

References:
- Skydroid S10 user manual copy: https://manuals.plus/ae/1005012249729278
- Skydroid official website: https://www.skydroid.xin/?lang=en

The manual and website are evidence of the utility's intended role and the vendor's distribution/support context. The original URL and acquisition date for this exact ZIP have not been recovered, and the exact supplied archive has not been independently matched against a current vendor-hosted download. Record this as maintainer-reported public-source provenance, not independently verified binary authenticity.

## Source and suitability

The archive was supplied by the project maintainer and is associated with the Skydroid S10 DeviceHelper updater. The original download URL, acquisition date, vendor signature status, exact application version, and authorized redistribution terms have not been independently confirmed.

The executable appears to include serial-port and firmware-update related code. Exact supported models, transport settings, update protocol, and firmware compatibility remain unverified. Do not describe it as universal for S10-family devices without evidence.

## Redistribution status

The original ZIP and executable are **not included in this public repository at present** because redistribution permission has not been established. Public availability on a vendor website is useful provenance evidence, but does not by itself establish permission to mirror the binary. If permission or an applicable licence is confirmed, publish the exact unmodified artifact with these hashes and a clear source/provenance record. Otherwise retain the metadata and analysis here, and direct readers to an authorized vendor download if one can be verified.

## Safety disclaimer

This is an independent research project, not affiliated with or endorsed by Skydroid. Treat vendor executables cautiously. Static-analysis notes are not a security audit. Do not run the updater or use it for a firmware update unless the source, device model, firmware image, power stability, and recovery plan have been checked.
