# Be10X · Payment Batch Splitter

A single-page web app that splits Juspay/GKL payment reports into multiple CSVs — one per batch group — based on the Batch Change time ranges.

## 🚀 Deploy to GitHub Pages

1. **Create a new GitHub repository** (public or private)
2. **Upload both files** to the repo root:
   - `index.html`
   - `README.md`
3. Go to **Settings → Pages**
4. Under "Source", select `main` branch → `/ (root)` → **Save**
5. Your app will be live at: `https://yourusername.github.io/repo-name`

---

## 📋 How to Use

### Step 1 — Upload Files
| File | Description |
|------|-------------|
| `Batch_Change.csv` | Time ranges per group (from inclusive → to exclusive) |
| `payment_report_Juspay_*.csv` | Juspay payment export with `CreatedAt` column |

### Step 2 — Configure Output
| Field | Description |
|-------|-------------|
| `wsdt` | Workshop date/time (e.g. `29th March \| 11 AM`). If blank, uses Batch_name. |
| `brname` | Brand name (default: `Be10X`) |
| `calendar` | Calendar link. If blank, uses WA GROUP from batch file. |
| `flink` | Follow-up form link |

### Step 3 — Process & Download
- Click **Split Payments by Batch**
- See summary table with payment count per group
- Download individual CSVs per group **or** all groups as a ZIP

---

## 📄 Output Format

Each CSV matches the Main Data format:

| Column | Source |
|--------|--------|
| Name | (empty) |
| CountryCode | Extracted from phone (91 for India) |
| Phone | 10-digit number |
| AllowBroadcast | True |
| AllowSMS | True |
| emailid | From payment Email |
| Amount | From payment Amount |
| wsdt | Config or Batch_name |
| brname | Config (default: Be10X) |
| calendar | Config or WA GROUP from batch |
| flink | Config |

---

## ✅ Handles

- Messy/typo dates in Batch CSV (e.g. `27/05/25023`, `29/122023`, dot separators)
- Phone numbers with `+91`, quotes, or without country code
- Payments that don't match any batch (grouped as "Unmatched")
- Last batch row with no `to (exclusive)` date (open-ended)
- ZIP download for all groups at once

---

## 🔒 Privacy

All processing happens **in your browser**. No data is uploaded to any server.

---

*Built for House of EdTech · Be10X*
