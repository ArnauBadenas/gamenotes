---
title: My games notes
---

This are my game notes.

{{ range sort (where .Site.Pages "Params.type" "eq" "index") ".Title" "asc" }}
- [{{ .Title }}]({{ .RelPermalink }})
{{ end }}

