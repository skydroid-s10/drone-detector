# Archive release and provenance policy

This project aims to make firmware research reproducible while keeping the source and status of every artifact clear.

## Classify every artifact

Use one of these labels:

- **Verified vendor source** — provenance supported by a trustworthy vendor source or verifiable vendor signature.
- **Maintainer-supplied, source unverified** — supplied by a project maintainer, but original provenance not independently confirmed.
- **Modified/reconstructed** — changed from the original; document exactly how and from what.
- **Unknown** — origin or relationship to a claimed release is not established.

Never promote an artifact to “official” solely because of its filename, version string, or resemblance to another file.

## Required record

For each binary, record its exact filename, byte size, SHA-256, acquisition source/date, claimed model and version, observed hardware compatibility, signature/integrity observations, and redistribution permission. Separate reported information from independently verified facts.

## Public redistribution gate

Before committing vendor firmware, executables, DLLs, drivers, or other bundled binaries, establish a clear licence or permission basis that allows public redistribution. A research purpose, archive label, disclaimer, or checksum does not by itself grant that permission.

If permission is unclear, publish the metadata, hashes, independently written analysis, and authorized-source links instead of the binary. Revisit the decision when permission is confirmed.

## Compatibility and safety

Compatibility must be stated narrowly and backed by evidence. A file tested on one S10G2 hardware revision is not thereby validated for other S10/S10G2 variants. Do not claim modified firmware is flash-ready until format, integrity, compatibility, and recovery have been established.

This repository is independent and is not endorsed by the vendor. Users are responsible for verifying artifacts and following safe update procedures.
