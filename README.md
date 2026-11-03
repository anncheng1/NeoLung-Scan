# NeoLung Scan

Step-by-step neonatal lung ultrasound acquisition on a phone, following the **Pleura-ABCDE** protocol. For each lung zone the app guides probe placement, takes a snapshot of the ultrasound screen, records the Pleura-ABCDE findings and a 0–3 zone score. Each examination exports as one ZIP (PDF protocol, images by zone, `metadata.json`, `findings.csv`) for upload to Google Drive and later AI image review.

![NeoLung Scan](icons/icon-192.png)

Part of the NeoLung AI project, Department of Paediatrics and Neonatology, Hospital Miri.

**Open the app:** https://anncheng1.github.io/NeoLung-Scan/

> Research prototype. Not a validated medical device. No severity category or treatment threshold is applied.

## Install on a phone

- **iPhone (Safari):** open the link, tap **Share**, then **Add to Home Screen**, then **Add**. Open **NeoLung** from the home screen and always scan from there: examinations saved in the home-screen app stay there, work offline and are not cleared by Safari.
- **Android (Chrome):** open the link, tap the **⋮** menu, then **Install app** or **Add to Home screen**.

After the first visit the app works offline.

## How an examination runs

1. **New examination:** study ID, baby and clinical details, 6 zones (anterior and lateral, score 0–18) or 10 zones (adds posterior).
2. **For each zone:**
   1. Place the probe (diagram, landmarks, settings).
   2. Snapshot: take a photo of the frozen ultrasound screen or upload an exported image or clip, crop to the scan area, confirm four quality checks (one tap when all are OK).
   3. What do you see? Tap the main pattern (Normal, Spared B-lines, White lung, Consolidation). It fills in all Pleura-ABCDE findings and the score; adjust any finding that differs.
   4. Zone score 0–3 (Brat et al. 2015), suggested from the findings.
3. **Review and export:** findings table, score, interpretation, then **Download ZIP for Google Drive**.

## Export contents

```
STUDYID_YYYYMMDD-HHMM/
├── STUDYID_YYYYMMDD-HHMM_protocol.pdf
├── images/STUDYID_YYYYMMDD-HHMM_R1-RUA_1.jpg …
├── metadata.json      # each image linked to zone, findings, score, quality checks
├── findings.csv
└── README.txt
```

## Privacy

- Examinations and images are stored only in the browser on the device (IndexedDB). Nothing is sent to a server.
- Patient name, registration number and date of birth stay on the device. They appear in the PDF only if the user ticks the option, and never in images or `metadata.json`.
- Crop each snapshot so no patient identifiers remain in the image.
- Use a hospital-approved Google Drive account for uploads, and follow local data governance approval before use with real patients.

## Files

| Path | Purpose |
| --- | --- |
| `index.html` | The app |
| `refs.js` | Reference ultrasound images (Pleura-ABCDE figures) |
| `sw.js`, `manifest.webmanifest`, `icons/` | Installable offline web app |
| `vendor/` | JSZip 3.10.1 and jsPDF 2.5.1 (MIT) |

## Credits

- Protocol and reference images: Sandig J, Küng E, Aichhorn L, et al. *Pleura-ABCDE – a structured expert-based protocol for neonatal lung ultrasound documentation and interpretation.* Ultrasound J. 2025;17:48. doi:10.1186/s13089-025-00442-4. Licensed [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); images were resized for the app.
- Score: Brat R, Yousef N, Klifa R, et al. *Lung ultrasonography score to evaluate oxygenation and surfactant need in neonates treated with CPAP.* JAMA Pediatr. 2015;169(8):e151797.
- Libraries: [JSZip](https://stuk.github.io/jszip/), [jsPDF](https://github.com/parallax/jsPDF) (MIT).

## License

App code: MIT (see `LICENSE`). Reference images: CC BY 4.0, as credited above.
