# License Policy

Rules for handling licenses when copying resources from external sources into the repository.

## Procedure

1. Copy the LICENSE file from the source into the plugin directory as `plugins/<plugin-name>/LICENSE`.
2. Set the `license` field in `plugin.json` to the correct SPDX identifier.
3. Check whether the license is permissive. If not, warn the user and wait for confirmation before proceeding.

## Permissive Licenses

The following SPDX identifiers are considered permissive:

- `MIT`
- `BSD-2-Clause`
- `BSD-3-Clause`
- `Apache-2.0`
- `ISC`
- `Unlicense`
- `0BSD`
- `CC0-1.0`
- `CC-BY-4.0`

## Non-Permissive License Warning

If the license is copyleft (`GPL-*`, `AGPL-*`, `MPL-*`, `LGPL-*`, `CC-BY-SA-*`) or not in the permissive list above, present this warning:

> **Warning: The source uses `<license>`, which is not a permissive license. This may impose obligations on the repository (e.g., derivative work must use the same license). Proceed?**

Do not create any files until the user explicitly confirms.

## Unknown Licenses

If no LICENSE file exists in the source or the license cannot be identified:

> **Warning: No recognizable license found in the source. Copying without a license may violate the author's copyright. Proceed?**

Ask the user to clarify the licensing situation before continuing.
