# n8n-Workflow-Definitionen

Forschungsartefakte zum Paper *End-to-End AI-Workflow-Automatisierung im
deutschen Mittelstand: Design und Evaluation eines Prototyps*
(Himmelstein & Krieger, 2026).

Dieses Verzeichnis enthält die im Rahmen der Fallstudien entwickelten
n8n-Workflows als importierbare JSON-Exporte. Es handelt sich um
**Forschungsprototypen, nicht um produktionsreife Software**.

## Enthaltene Workflows

| Datei | Fallstudie | Zweck | Erforderliche Zugänge |
| --- | --- | --- | --- |
| `fall-a_preistraeger-scout.json` | A | Websuche nach Preisverleihungen, LLM-gestützte Extraktion von Unternehmen, Deduplizierung, Excel-Ausgabe | n8n, Brave Search API, SerpAPI, Anthropic API |
| `fall-b_newsletter-generator_url-freitext.json` | B | URLs und Freitext → strukturierter Newsletter (DOCX) + LinkedIn-Beitrag | n8n, Anthropic API, Mistral (OCR) |
| `fall-b_newsletter-generator_pdf.json` | B | PDF-Quellen → Newsletter + LinkedIn-Beitrag | n8n, Anthropic API, Mistral (OCR) |
| `fall-e_wissensagent_sprachinterview.json` | E | Transkript eines sprachbasierten KI-Interviews → How-To-Dokumentation im Word-Format | n8n, Vapi, Anthropic API |


## Import

n8n öffnen → *Workflows* → *Import from File* → JSON auswählen.

Die Workflows sind nach dem Import bewusst **inaktiv** (`active: false`).
Vor der ersten Ausführung sind eigene Zugangsdaten zu hinterlegen.

## Zugangsdaten

Sämtliche Anmeldedaten wurden vor der Veröffentlichung entfernt. Es gibt
zwei Stellen, an denen eigene Zugänge zu ergänzen sind:

1. **n8n-Credentials** — Nodes vom Typ *Anthropic Chat Model* und
   *Mistral* referenzieren benannte Credentials (z. B. `Anthropic account`).
   Diese sind in der eigenen n8n-Instanz einmalig anzulegen und den Nodes
   zuzuweisen.
2. **Umgebungsvariablen** — an den übrigen Stellen wurde auf
   `$env.<NAME>` umgestellt. Zu setzen sind je nach Workflow:
   `ANTHROPIC_API_KEY`, `BRAVE_API_KEY`, `SERPAPI_KEY`, `GEMINI_API_KEY`.
   Der Zugriff auf Umgebungsvariablen aus Code-Nodes setzt voraus, dass
   `N8N_BLOCK_ENV_ACCESS_IN_NODE=false` gesetzt ist.

Platzhalter in spitzen Klammern (`<ihre-n8n-instanz>`,
`<ihr-frontend-host>`, `<VAPI_ASSISTANT_ID>`) sind durch eigene Werte zu
ersetzen. Die Webhook-URLs sind instanzspezifisch und werden von n8n nach
dem Import neu vergeben.

## Anonymisierung

Die Workflows enthalten keine Daten der in den Fallstudien beschriebenen
Unternehmen. Bezeichnungen, Beispieldaten und Prompts wurden so gefasst,
dass keine Rückschlüsse auf die beteiligten Organisationen möglich sind.

## Lizenz

MIT (siehe `LICENSE`).

## Zitation

> Himmelstein, N. & Krieger, F. (2026). *Workflow-Definitionen und
> Prototypen zu „End-to-End AI-Workflow-Automatisierung im deutschen
> Mittelstand"* [Software]. Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX
