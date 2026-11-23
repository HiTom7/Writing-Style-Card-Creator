# Revisione della localizzazione italiana (it)

## Ambito

Sono stati usati i testi inglesi come origine e completati i punti rimasti in inglese o privi di una voce italiana. Gli interventi includono:

- regole per i canali e i formati;
- schede dei ruoli e attività professionali con relative strategie;
- indicazioni per i profili politico e persona;
- preset del modello, etichette di strategia e indicazioni anti-cliché IA;
- testi del flusso, nomi e descrizioni dei preset e regole iniziali dei preset;
- pack completo dell’esportazione, incluse avvertenze legali e mediche e prompt di sistema;
- testi di fallback dell’interfaccia per persona, canali, prompt, modalità semplificata e attivazione Pro.

## Verifiche

- `node --check` sul JavaScript incorporato: superato.
- `git diff --check`: superato.
- Nessun dizionario con chiave inglese è rimasto senza la corrispondente voce italiana.
- Le quantità delle opzioni di stile e gli identificatori delle attività professionali coincidono con la versione inglese.
- Le chiavi del pack di esportazione italiano corrispondono a quelle spagnole già complete.

## Limiti

Revisione statica; non è stato eseguito un test completo interattivo del browser né una revisione da parte di un madrelingua. I controlli strutturali verificano la copertura e l’allineamento delle chiavi, non la perfezione editoriale di ogni frase o tutte le combinazioni di esportazione.
