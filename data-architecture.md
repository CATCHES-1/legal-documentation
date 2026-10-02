# Data Architecture and Brand Integration Framework

**CATCHES Limited · Internal and confidential · Version 2.0, 2 October 2026**

## 1. Principles

1. CATCHES is the independent controller of Widget Data (photos, measurements, biometric data, Visuals and accounts). The brand is the controller of Site Data; CATCHES uses Site Data only to run the service and calculate fees.
2. No photo is processed without a recorded biometric consent.
3. Photos, measurements and biometric data are never used for model training.
4. Brand data is kept separate: brand-specific models, weights and garment builds are never used for another brand.
5. Delete by default: session data 30 days after last use; biometric data no later than 24 months after last interaction.

## 2. User data architecture

### 2.1 Standing notice (all users)

The widget shows a persistent line: "Powered by CATCHES. AI-generated try-on. [Privacy Policy] · [Biometric Notice] · [Terms]". This provides transparency for non-photo use (avatar selection, size, measurements and technical data). Measurements are processed on consent, given when the user enters them; technical data on legitimate interests.

### 2.2 Photo upload without an account (session mode)

When a user chooses to upload a photo, the widget shows this disclosure above three required checkboxes:

> "When you upload a photo, CATCHES Limited derives measurements of your body geometry and proportions from it to create your virtual try-on. This may be biometric data, and we treat it as biometric data. We use it only to show you the try-on, never to identify you or to train AI models, and we delete it 30 days after your last interaction. See our Privacy Policy, Biometric Notice and Terms."

- Checkbox 1: "I am 18 or over, and this photo is of me."
- Checkbox 2: "I agree to the CATCHES Terms."
- Checkbox 3: "I consent to CATCHES collecting and using my biometric data as described above."

**Consent logging.** Each consent is stored as a record: pseudonymous user or session ID, timestamp, notice version ID, checkbox wording, widget version, brand storefront and jurisdiction (from IP). Records are kept for 5 years.

**Version control.** Every change to the disclosure or checkbox wording gets a new version ID. Old versions are archived with their live dates.

### 2.3 Age protection

1. Users self-certify their age (checkbox 1).
2. Automated screening flags photos that appear to show someone under 18. A flagged photo is blocked and discarded.
3. A flagged user can still use avatars and size-based features.
4. Photo features stay blocked for a flagged user unless they pass an age check (automated age estimation using AI). Email verification alone is not enough.

### 2.4 Accounts (persistent mode)

Account creation shows the same disclosure, with the retention line replaced by: "As an account holder, we keep your digital model until you delete it or withdraw consent. If you do not use CATCHES for 24 months, we delete it automatically." Account holders can withdraw biometric consent without deleting the account. Withdrawal purges biometric data, photos and measurements within 30 days, and photo features revert to session mode. Cross-brand personalisation is a separate, optional consent, off by default.

### 2.5 Retention jobs

| Data | Trigger | Deletion |
| --- | --- | --- |
| Session photo, measurements, biometric data, Visuals | 30 days after last interaction | Automated daily job |
| Account biometric data | Withdrawal, account deletion or 24 months' inactivity | Within 30 days |
| Quality-review sample of Visuals | 90 days after sampling | Automated |
| Technical logs | 30 days | Then de-identified |
| Order and attribution data | 24 months | Pseudonymised while held |
| Consent records | 5 years | Then deleted |
| Backups | Rolling | Overwritten within 35 days |

The privacy team runs an annual biometric retention review. Anything no longer needed is deleted within 45 days.

## 3. Brand integration architecture

### 3.1 Components

- **CATCHES Snippet**: a JavaScript tag on the brand's product pages. It loads the Launch Button and widget and records Launch Button impressions and Interactions. It does not read other page content, form fields or browsing outside the widget.
- **Widget (iframe)**: runs on CATCHES infrastructure. Widget Data goes from the user directly to CATCHES and is never stored by the brand.
- **CATCHES Identifier**: after an Interaction, a code is added to the user's cart or order in the brand's ecommerce platform (for example as a Shopify cart or order attribute). It stays for at least 30 days after the last Interaction.
- **Order connector**: a read-only platform app or API connection. For orders carrying the CATCHES Identifier, it receives order ID, date, value, currency, discounts, items, quantities and returns. It never receives names, addresses or payment details.

### 3.2 Cookies and consent gating

| Cookie | Purpose | Duration | Consent category |
| --- | --- | --- | --- |
| c-user | Authentication | 24 hours | Strictly necessary |
| c-user-ref | Session refresh | 30 days | Strictly necessary |
| _dd_s | Real user monitoring | Up to 4 hours | Performance; gated by the brand's consent tool |

The Snippet reads the brand's consent signal and Global Privacy Control. The Launch Button may display before consent, but no Guest Profile or performance cookie is set until the signal permits.

### 3.3 Roles and data flows

| Data | Controller | CATCHES role | Used for |
| --- | --- | --- | --- |
| Widget Data | CATCHES | Controller | Generating Visuals; accounts |
| Site Data (impressions, Interactions, CATCHES Identifier, order data) | Brand | Service provider / processor | Running the service; fees; reports |
| Usage data, de-identified | CATCHES | Controller | Measurement and improvement |
| Collection through the widget (UK/EEA) | Joint, under the brand agreement's joint-controller schedule | Presents notices and consents; handles requests | Collection and transmission |

### 3.4 Measurement and comparison groups

Uplift reviews split traffic into a group shown the Launch Button and a comparison group not shown it. Up to 10% of traffic may be held out for ongoing monitoring. Only group membership is recorded.

### 3.5 Brand data separation

Garment builds, brand-specific model tunes and Product Information are stored in a separate namespace for each brand, with access limited to that brand's pipeline. Any model artefact trained on one brand's data carries the brand tag and is blocked from use for other brands.

### 3.6 Security and subprocessors

The controls in section 6 of the Privacy Policy apply. A list of subprocessors is available on request from privacy@catches.ai, and brands receive 30 days' notice before a new one is added. Brand Materials are classified Restricted. Security incidents are reported to the affected brand within 72 hours.
