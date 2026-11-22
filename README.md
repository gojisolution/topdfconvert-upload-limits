# ToPDFConvert upload limits: official file rules for visa and government portals

File size limits and file rules for online portals where people upload documents: visa, immigration and benefit applications. Every value is read on the **authority's own page**, never copied from another website, and carries the **date we checked it** and the **link to that page**.

Rejected uploads are mostly about size, file type or a password on the PDF. Some lists online give old numbers (for example 6 MB for USCIS, which now says 12 MB). This dataset exists so that one list stays current and can be checked line by line.

| Portal | Country | Limit per file | Also required | Checked |
|---|---|---|---|---|
| [NVC / CEAC](https://travel.state.gov/content/travel/en/us-visas/immigrate/the-immigrant-visa-process/step-1-submit-a-petition/step-2-begin-nvc-processing/scanning-and-uploading-tips.html) | US | 2 MB | JPG or PDF, one document per file, 150 DPI, no password | 2026-11-20 |
| [USCIS online filing](https://www.uscis.gov/file-online/tips-for-filing-forms-online) | US | 12 MB | PDF, JPG or JPEG (TIFF for some forms), no password or encryption | 2026-11-21 |
| [IRCC secure account, citizenship, asylum, PR portal](https://ircc.canada.ca/english/helpcentre/answer.asp?qnum=1123) | CA | 4 MB | – | 2026-11-21 |
| [IRCC Portal, new and old version](https://ircc.canada.ca/english/helpcentre/answer.asp?qnum=1123) | CA | 5 MB | – | 2026-11-21 |
| [Meu INSS](https://www.gov.br/inss/pt-br/noticias/precisa-cumprir-exigencia-saiba-como-realizar-o-procedimento) | BR | 5 MB | PDF, scanned in colour, whole document in frame | 2026-11-21 |
| [Indian e-Visa](https://indianvisaonline.gov.in/evisa/tvoa.html) | IN | 10–300 KB | Documents as PDF; the photo is a separate JPEG of 10 KB to 1 MB | 2026-11-20 |

## Files

- [`portal-limits.json`](portal-limits.json): the full data, one object per portal.
- [`portal-limits.csv`](portal-limits.csv): the same, for spreadsheets.
- [`CHANGELOG.md`](CHANGELOG.md): every re-check and change, with its date.

## Fields

| Field | Meaning |
|---|---|
| `id` | Stable identifier, e.g. `us-uscis` |
| `portal`, `country`, `authority` | Which portal, its ISO country code and who publishes the rule |
| `max_bytes_per_file`, `min_bytes_per_file` | Limits in bytes, **decimal** (1 MB = 1,000,000 bytes), which is safe whether a portal counts in decimal or binary megabytes |
| `limit_text` | The same limit as a short text, e.g. `12 MB` |
| `accepted_formats`, `formats_for_some_forms_only` | File types the page names (`pdf`, `jpg`, `tiff`) |
| `password_protected_allowed` | `false` when the page says not to upload protected files |
| `one_document_per_file`, `scan_dpi`, `colour_scan` | Other requirements stated on the page |
| `notes` | The rule in plain words |
| `source_url`, `checked` | The authority's page and the date (YYYY-MM-DD) we read it |

`null` means the official page does not say. We leave a value out rather than guess.

## How the data is kept

- A rule is added only when the authority's own page states it. Third-party guides are never a source.
- Each rule is re-checked on its source page; the date in `checked` changes only after that.
- The portal always decides what it accepts, and some documents have extra instructions inside the application itself. Read those too.

Seen a rule change, or know an official page with upload limits that should be here? [Open an issue](../../issues) with the link to the official page.

## Use it

The data is free to use under [CC BY 4.0](LICENSE). Please credit **ToPDFConvert (topdfconvert.com)** with a link.

The same rules power two free tools on [topdfconvert.com](https://topdfconvert.com): the [upload checker](https://topdfconvert.com/upload-checker), which tells you before you upload what a portal would refuse, and [Compress PDF](https://topdfconvert.com/compress-pdf), which makes a PDF fit a portal's limit. Both run in your browser, so your documents are not uploaded.
