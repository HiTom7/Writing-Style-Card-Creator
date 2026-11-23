# Prüflauf der deutschen Lokalisierung (de)

## Umfang dieser Sprachrunde

Die englischen Ausgangstexte wurden als Referenz verwendet; fehlende deutsche Einträge wurden gezielt ergänzt, statt vorhandene polnische oder französische Fassungen als Quelle zu verwenden. Ergänzt wurden insbesondere:

- deutsche Exporttexte für alle sechs Kartenebenen einschließlich rechtlicher/medizinischer Hinweise und System-Prompt;
- bislang fehlende Kanal- und Formatregeln;
- Rollen-Playbooks und professionelle Aufgabenbeschreibungen samt Strategien;
- Modell-/Humor-Presets, Strategie- und Anti-KI-Bezeichnungen sowie Workflow-Texte;
- alle neun Gruppen von Schreibstiloptionen sowie Beschriftungen und Metadaten der Stilbereiche;
- deutsche Texte für Preset-Regeln und zuvor englische UI-Fallbacks.

## Prüfungen

- `node --check` für das eingebettete JavaScript: erfolgreich.
- `git diff --check`: erfolgreich.
- AST-Prüfung: keine englischsprachigen Wörterbuchobjekte ohne deutschen Eintrag gefunden.
- Die Anzahlen der deutschen und englischen Stiloptionen stimmen überein.
- Die Aufgaben-IDs der deutschen Rollenaufgaben stimmen mit den englischen IDs überein.

## Grenzen

Statische Prüfung; kein vollständiger manueller Browser-Durchlauf und keine native sprachliche Abnahme. Die Strukturprüfungen bestätigen Abdeckung und Zuordnung, nicht die redaktionelle Perfektion jeder Formulierung oder jede Kombination im Export.
