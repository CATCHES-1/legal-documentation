# CATCHES legal documentation

Public legal documents for CATCHES Limited (company number 10804799).

Until CATCHES announces otherwise, the authoritative versions are published at [docs.catches.ai/legal-documentation](https://docs.catches.ai/legal-documentation). This repository holds the same text with a full change history.

## Latest versions

These files always hold the current text of each document.

| Document | File |
| --- | --- |
| CATCHES User Privacy Policy | [privacy-policy.md](privacy-policy.md) |
| CATCHES Biometric Notice | [biometric-notice.md](biometric-notice.md) |
| CATCHES Brand Terms of Use | [brand-terms-of-use.md](brand-terms-of-use.md) |
| CATCHES End User Terms | [end-user-terms.md](end-user-terms.md) |
| Data Architecture and Brand Integration Framework | [data-architecture.md](data-architecture.md) |
| Our Position on Privacy, AI, and Trust and Safety | [privacy-ai-trust-safety.md](privacy-ai-trust-safety.md) |

## Version history

Each published version is a release tag. A tag is never moved or deleted once created, so a link to a tag always shows the text as it was on that date.

| Version | Published | What changed |
| --- | --- | --- |
| [v2026-10-02](https://github.com/CATCHES-1/legal-documentation/tree/v2026-10-02) | 2 October 2026 | First version in this repository. Text matches docs.catches.ai on this date. |
| [v2026-10-02.2](https://github.com/CATCHES-1/legal-documentation/tree/v2026-10-02.2) | 2 October 2026 | Privacy Policy, Biometric Notice and Data Architecture framework updated to version 2.0. Terms of Service replaced by the Brand Terms of Use (`brand-terms-of-use.md`). End User Terms added. |

## Link to a specific version

To reference a document in a contract, link to it at a release tag rather than at `main`:

    https://github.com/CATCHES-1/legal-documentation/blob/v2026-10-02/terms-of-service.md

To see every change between two versions, compare their tags:

    https://github.com/CATCHES-1/legal-documentation/compare/v2026-10-02...vYYYY-MM-DD

## Publish a new version

1. Open a pull request against `main` with the changed documents, using the pull request template.
2. In the same pull request, update the "Last updated" line in each changed document and add a row to the version history table above.
3. Get approval from a code owner. The `main` branch accepts changes only through an approved pull request.
4. Merge the pull request.
5. Create a release tag named `vYYYY-MM-DD` on the merge commit, using the publication date.

## Copyright

© 2026 CATCHES Limited. All rights reserved.

These documents are published so that users, brand partners and regulators can read them. No licence is granted to copy, adapt or reuse them.
