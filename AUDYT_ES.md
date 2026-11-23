# Audyt lokalizacji hiszpańskiej (es)

## Zakres etapu

Przegląd dotyczył hiszpańskiej ścieżki aplikacji oraz treści generowanych/eksportowanych. Uzupełniono i poprawiono m.in. teksty pomocy i interfejsu, komunikaty walidacji/aktywacji Pro, etykiety eksportu, preset persony oraz zestawy wskazówek ról. To przegląd statyczny w wybranych mapach i ścieżkach, nie certyfikacja native speakera ani pełny przegląd każdej hiszpańskiej frazy w całym pliku.

## Walidacja

- Skrypt JavaScript osadzony w `index.html`: `node --check` — poprawny.
- `git diff --check` — poprawny.
- AST: występują mapy i słowniki bez hiszpańskich odpowiedników (część jest historycznym fallbackiem/inaczej modelowanymi danymi); to nie jest dowód pełnego pokrycia lokalizacji.
- Pełny przepływ eksportu i interaktywny test w przeglądarce nie zostały zweryfikowane w tym etapie.

## Uwagi

Eksport powinien korzystać z tekstów wybranych zgodnie z ustawionym językiem; w tym etapie poprawiono istniejące hiszpańskie teksty eksportu, bez deklarowania, że każdy wariant eksportu został ręcznie sprawdzony.
