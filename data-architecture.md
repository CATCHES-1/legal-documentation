# Data Architecture and Brand Integration Framework

CATCHES Limited  \|  April 2026

**User data architecture**

**Notice and consent architecture**

The VTO Widget displays a standing notice where a privacy policy link would typically appear: "By using this widget you acknowledge the terms of the [CATCHES Privacy Policy](privacy-policy.md)". This is a persistent disclosure visible on the widget interface, not a click-through gate. It provides transparency and incorporates the privacy policy by reference.

**Without an account (session-based)**

The user receives all features: avatar selection, size and body measurements, photo upload with advanced processing, and AI-generated virtual try-on results. For non-photo interactions (avatar selection, size, measurements, technical data), the lawful basis is legitimate interests (GDPR Art. 6(1)(f)) and the standing notice described above is sufficient.

When a user without an account elects to upload a photograph, a disclosure block is displayed above two required checkboxes:

**Disclosure:** "When you upload a photo, CATCHES Limited derives body geometry, physical characteristics, and body composition measurements from your image to generate a virtual try-on avatar. This category of data may be classified as biometric data under certain applicable laws; regardless of classification, CATCHES treats it as biometric data and protects it accordingly. This data is deleted 30 days after your last interaction with the service. To learn more, please review our [Privacy Policy](https://docs.catches.ai/catches-app-privacy-policy-sh) and [Biometric Notice](biometric-notice.md).”

**Checkbox 1:** "I certify that I am 18 years of age or older and I have read the Privacy Policy and Biometric Notice."

**Checkbox 2:** "I consent to the collection and processing of my biometric data."

This satisfies BIPA Section 15(b) (written notice of collection, purpose, and term preceding written release) and GDPR Art. 9(2)(a). All data is ephemeral. Photographs and derived data are deleted 30 days after your last interaction with the service. Technical data is retained for up to 30 days. The system architecturally cannot process a photograph without both checkboxes, meaning the existence of any biometric data is itself evidence that consent was obtained.

**Age protection**

In addition to the checkbox age certification, CATCHES' photo upload system uses AI-based detection to flag photographs it believes depict individuals under 18. If a photo is flagged, the upload is blocked for that session. The user can still access the widget using avatar selection, size, and body measurements, but cannot use photo-based features. If a flagged user wants photo features, they must create an account, which adds email verification as an additional friction layer. This produces a layered defense: (1) checkbox self-certification, (2) AI photo detection, (3) flagged users blocked from photo upload in session mode, and (4) account creation with email verification as the only path to photo features for flagged users.

**With an account (persistent)**

Account creation has its own consent flow. A disclosure is displayed, followed by required affirmative consents:

**Disclosure:** "When you upload a photo, CATCHES Limited derives body geometry, physical characteristics, and body composition measurements from your image to generate a virtual try-on avatar. This category of data may be classified as biometric data under certain applicable laws; regardless of classification, CATCHES treats it as biometric data and protects it accordingly. As an account holder, this data is retained for up to 3 years. Before the expiration of this period, CATCHES will notify you and request renewed consent. If you do not renew, your biometric data will be permanently deleted. To learn more, please review our [Privacy Policy](https://docs.catches.ai/catches-app-privacy-policy-sh) and [Biometric Notice](biometric-notice.md).”

**Checkbox 1:** "I certify that I am 18 years of age or older and I have read the Privacy Policy and Biometric Notice."

**Checkbox 2:** "I consent to the collection, processing, and retention of my biometric data as described above."

Account holders receive all session-based features plus: persistent storage of the digital twin, persistent photographs and measurements, and cross-brand personalization (scope pending). Cross-brand personalization is optional and is not a condition of using the Service.

Account holders may withdraw biometric consent without deleting their account. Withdrawing biometric consent triggers a purge of all stored biometric data, photographs, and derived measurements. The account is retained and photo features revert to session-only mode.

CATCHES should maintain version control of all consent text so it can demonstrate what language was live at any given time. All features, including advanced biometric processing, are available to all users regardless of whether they create an account. The distinction between account and non-account users is persistence and ecosystem access, not feature availability.
