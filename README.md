# veda-ai-feedback

Shared problem-report desk for all VEDA AI services:

- EWAia Abbreviation Search
- Veda Bib
- Veda Image
- Text Image Viewer
- VEDA AI Reader
- Text Search
- Gandhari Converter
- Project site
- Other

## Before you report

- A GitHub account is required.
- Issues in this repository are **public**. Do not include personal or confidential information.
- The form is bilingual (English / 日本語). You may write in either language.

## Report a problem

<https://github.com/Yuzki/veda-ai-feedback/issues/new?template=problem-report.yml>

## Linking from a service (prefilled form)

```
https://github.com/Yuzki/veda-ai-feedback/issues/new?template=problem-report.yml&service=<SERVICE>&page=<PAGE_URL>
```

- Query parameter names are the form field ids: `service` and `page`. The other fields can be prefilled too: `problem_type`, `description`, `expected`, `environment`.
- `service` must equal a dropdown option exactly (case-sensitive) and be URL-encoded. An unknown value leaves the dropdown unselected, so the user picks it manually.
- `page` must be percent-encoded (`encodeURIComponent`), e.g. `page=https%3A%2F%2Fexample.org%2Fviewer%3Fid%3D1%23p2`.
- Do not use the `labels=` parameter; it only works for users with triage rights.

| `service` value | Encoded |
| --- | --- |
| EWAia Abbreviation Search | `EWAia%20Abbreviation%20Search` |
| Veda Bib | `Veda%20Bib` |
| Veda Image | `Veda%20Image` |
| Text Image Viewer | `Text%20Image%20Viewer` |
| VEDA AI Reader | `VEDA%20AI%20Reader` |
| Text Search | `Text%20Search` |
| Gandhari Converter | `Gandhari%20Converter` |
| Project site | `Project%20site` |
| Other | `Other` |

JavaScript snippet for a service page:

```js
const base = "https://github.com/Yuzki/veda-ai-feedback/issues/new";
const url = `${base}?template=problem-report.yml&service=${encodeURIComponent("Veda Bib")}&page=${encodeURIComponent(location.href)}`;
```

Stability: the field ids and the `service` option strings are a public contract used by these URLs. Do not rename them. To add a service, add the dropdown option, create its label, and add a row to the table above.

## Labels (maintainer setup)

Create the labels once:

```sh
gh label create "service: EWAia Abbreviation Search" --color 1d76db --description "EWAia Abbreviation Search"
gh label create "service: Veda Bib" --color 1d76db --description "Veda Bib"
gh label create "service: Veda Image" --color 1d76db --description "Veda Image"
gh label create "service: Text Image Viewer" --color 1d76db --description "Text Image Viewer"
gh label create "service: VEDA AI Reader" --color 1d76db --description "VEDA AI Reader"
gh label create "service: Text Search" --color 1d76db --description "Text Search"
gh label create "service: Gandhari Converter" --color 1d76db --description "Gandhari Converter"
gh label create "service: project site" --color 1d76db --description "Project site"
gh label create "service: other" --color 1d76db --description "Other"
# optional
gh label create "type: data-error" --color d93f0b --description "Data error"
gh label create "type: display" --color d93f0b --description "Display issue"
gh label create "type: functional" --color d93f0b --description "Functional issue"
```

Triage: apply the label that matches the `service` field of each new issue. Automating this (e.g. with a GitHub Action) is out of scope for now.

## Maintainers: editing the form

The form is defined in `.github/ISSUE_TEMPLATE/problem-report.yml`; `config.yml` disables blank issues. Keep the field ids and service option strings unchanged (see above).
