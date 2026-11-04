# Changelog

All notable changes to `qalainau/filament-warp-markup` are documented here.

## [1.0.0] - 2026-11-05

### Added

- First release: drawing workspace (PDF and images), markup tools, findings as your own records, revisions with carry-over and comparison, export and findings report, form field.
- Areas (rooms): a `zone` tool draws named areas; findings know the area they are in (list, search, filter, report, CSV), `zones('room')` fills an attribute of new findings, and **Color by count** colors areas by their open findings.
- Links between drawings: a `link` tool opens another drawing or page, **Back** returns, and **Find links** turns sheet numbers in a PDF page's text into links. Page names come from the sheet number in each PDF page's title block, and new revisions keep them.
- Quantities: a `count` tool, a **Quantities** tab (counts, total lengths and areas, area of each named area) and a CSV of all pages.
- Change many findings at once (status, assignee, due date), from the list or by selecting pins on the drawing.
- `beforeStatusChange()` and `statusLocked()`: rules for status changes, for example a photo before *Fixed* or an approval with Warp Flow before *Verified*.
- `stamps()`: your own stamps, with `{date}` and `{user}`, or images.
- Photos: mark up a comment photo (the drawing shows on the thumbnail and in the report), and compare a photo with the first one.
- Compare: align two revisions with two points, and **Cloud the changes** draws revision clouds around what changed.
- Export the findings as CSV (Excel) or BCF 2.1 (BIM tools).
- `shareLinks()`: share chosen findings with people without an account; they reply with comments, photos and “Fixed”. Links expire and can be revoked.
- `FindingsDigest` and `php artisan warp-markup:digest`: each assignee gets one message a day with their overdue findings.
- Multi-tenancy: new findings belong to the current tenant (`BelongsTo`, `MorphTo` or `BelongsToMany`), findings are filtered by tenant, files are stored in a folder per tenant, and `scopeToTenant(false | relationship:)` turns scoping off or names the relationship. The owner and tenant of a drawing are stored as text, so integer, UUID and ULID keys all work.
- Upload a whole drawing set at once: files whose name or sheet number matches a drawing (`A-101_rev-C.pdf`) become its new revision, with a preview before uploading.
- `findingTemplates()`: common issues that fill the finding form — picked before dropping a pin or at the top of the form, with values the form does not have and a due date in days.
- `checklists()`: walk a checklist on the drawing or room by room (OK, Failed, N/A), make a pinned finding from a failed item, finish and reopen; results as CSV and in the findings report.
- `layers()`: put markups on layers, move them between layers, and hide layers per person.
- `pinTypes()`: a pin list (symbol + name) that people edit on screen. Pins show the chosen symbol instead of the number, a one-off symbol can be typed, and the symbol of a placed pin can be changed. The finding list, details, report, share page and CSV show the symbol. Also on `MarkupField`. `MarkupPinType::createDefaults()` adds starting rows.
- A summary by status, assignee, area, drawing and `summaryGroups()`, with the open findings week by week.
- Portal links: a share link that always shows everything assigned to one person or company (`Shares::syncPortals()` for changes made outside the workspace).
- `signOff()`: a hand-written sign-off at handover, stored with the statement and the counts, and printed in the findings report.
- Search the text of every page of a PDF drawing; matches are outlined on the drawing.
- `assistant()`: optional AI (Claude, or your own `MarkupAssistant` / `ReadsTitleBlocks`) that suggests the common issue and title from a photo and reads title blocks.
- `Revisions::createDrawing()` from code: the drawing belongs to the current tenant unless you pass `'tenant'` (or `'tenant' => null` for none), and unknown keys such as `owner_type` are refused instead of being ignored.
- German, French, Spanish, Italian, Brazilian Portuguese, Korean and Chinese (simplified and traditional) translations, next to English and Japanese. The messages for an unsupported file, an unreadable image and a share link without findings are translated too.
