# Audyt aplikacji — tłumaczenia, struktura i użyteczność

## Zakres i ograniczenia

Audyt wykonano statycznie na dostarczonym pliku `index.html` (aplikacja jednoplikowa, ok. 1,14 MB i 13,4 tys. linii) oraz przez kontrolę składni osadzonego JavaScriptu (`node --check`, bez błędów). Nie uruchomiono testów przeglądarkowych ani testów z native speakerami; ocena językowa jest więc eksperckim przeglądem widocznych przykładów i architektury tłumaczeń, a nie pełną korektą każdej z dziesiątek tysięcy etykiet/opcji. Nie zmieniano wszystkich przekładów automatycznie, bo masowa podmiana bez kontekstu mogłaby wprowadzić nowe błędy.

## Podsumowanie

Do repozytorium przywrócono pełną aplikację z załączonego `index(11).html` zamiast wcześniejszej strony-placeholder. Aplikacja jest rozbudowanym kreatorem, nie prostym 13-krokowym formularzem opisanym przez poprzednią wersję README. Interfejs zawiera obszerną warstwę i18n, wiele sekcji/trybów oraz eksport. Składnia JavaScriptu przechodzi kontrolę.

Najważniejsze ryzyka jakościowe to nierówne pokrycie językowe, rozproszone źródła tekstów (i18n, LOC, FLOW_LABELS, dodatkowe łatki) oraz brak gwarancji, że wszystkie widoczne treści są tłumaczone. Oprócz sześciu języków pierwotnie wymienionych w README picker i dane aplikacji obejmują liczne inne języki. Obecność języka w pickerze nie jest równoznaczna z pełną, zweryfikowaną lokalizacją.

## Tłumaczenia — ustalenia

### Architektura

- Tłumaczenia są rozłożone na kilka słowników i dodatkowe bloki dopisujące/uzupełniające dane. To utrudnia znalezienie jednej prawdy o pokryciu, wykrywanie brakujących kluczy i review zmian.
- Funkcja `L()` scala angielski pakiet bazowy z pakietem aktywnego języka. To użyteczny mechanizm awaryjny, ale brakujące tłumaczenie może po cichu wyświetlić angielski tekst w środku lokalnego interfejsu.
- Lista wyboru języka, aliasy przeglądarkowe i dostępne tłumaczenia nie są tym samym zbiorem. Wartości wykrywania języka, m.in. `en-US`, wymagają szczególnego sprawdzenia w całym przepływie: wybranie, zapis, renderowanie i fallback.
- Część tekstów jest dopisywana później przez rozbudowane mapy pakietów. W przyszłości należy zastąpić to pojedynczymi plikami JSON/JS na język z walidatorem kluczy.

### Konkretne przykłady do poprawy

- W polskich opisach sekcji występuje „fillery” (zapożyczenie z angielskiego); naturalniej: „wypełniacze”, ewentualnie „wtrącenia” zależnie od kontekstu.
- W hiszpańskim widnieje konstrukcja „¿Cómo de largas…?”, która brzmi nienaturalnie w wielu odmianach. Lepsza, neutralna wersja: „¿Qué longitud suelen tener tus oraciones y párrafos?”.
- W hiszpańskim „Lo que sueles no hacer” jest niezręczne. Lepsze: „Lo que normalmente evitas” / „Lo que sueles evitar”.
- W opisach francuskich pominięcie rodzajników w „Comment vous utilisez exemples concrets, données et comparaisons” jest błędem; naturalniej: „Comment vous utilisez des exemples concrets, des données et des comparaisons”.
- Warto rozstrzygnąć rejestr: część języków ma formę grzecznościową (francuskie „vous”, niemieckie „Sie”), część zwraca się bezpośrednio i nieformalnie (m.in. hiszpańskie „tus”, polskie „Twoje”). Konsekwencję należy utrzymać w całym kreatorze i eksportowanym dokumencie.
- Są angielskie terminy produktowe („handle”, „tagline”, „fillers”, „boosters”, „anti-LLM”) w tłumaczonych tekstach. Nie wszystkie wymagają przekładu, ale powinny mieć ustalone lokalne odpowiedniki albo krótkie objaśnienie.
- Zawartość użytkownika w eksporcie powinna pozostawać niezmieniona; teksty systemowe eksportu powinny natomiast mieć tę samą lokalizację i rejestr co UI.

### Zalecenia lokalizacyjne

1. Ustalić listę języków faktycznie wspieranych i oznaczyć poziom pokrycia; nie sugerować pełnej lokalizacji na podstawie samego wyboru języka.
2. Ujednolicić słowniki, dodać skrypt porównujący klucze z bazowym językiem i raportujący braki oraz teksty nieużywane.
3. Wykonać korektę native speakerów dla wszystkich widocznych treści, nazw opcji, podpowiedzi, walidacji, komunikatów, podsumowania i eksportu — osobno dla każdej odmiany/rejestru.
4. Dodać testy przełączania języka w połowie pracy i eksportu w każdym języku; sprawdzić długie niemieckie/francuskie etykiety, polskie znaki oraz RTL dla arabskiego.

## Struktura i użyteczność

### Mocne strony

- Jednoplikowa aplikacja nie wymaga instalacji ani procesu budowania; łatwo ją uruchomić lokalnie.
- Kreator prowadzi użytkownika przez profilowanie, daje wybór gotowych opcji oraz pole na własne instrukcje.
- Są widoczne funkcje ułatwiające korzystanie: pasek postępu, tryb uproszczony, regulacja rozmiaru tekstu, motyw jasny/ciemny i podgląd/eksport.
- Wprowadzane wartości są kodowane przy wstawianiu do wielu pól HTML (`escapeHtml`/`escapeAttr`), co ogranicza ryzyko interpretacji danych jako markup w tych miejscach.

### Problemy i ryzyka UX

- Pojedynczy plik o rozmiarze ponad 1 MB i ponad 13 tys. linii łączy markup, CSS, bardzo duże dane tłumaczeń i logikę. Trudno go utrzymywać i testować; zalecany jest podział na moduły/słowniki, nawet jeśli dystrybucja nadal będzie mogła być spakowana do jednego HTML.
- Rozbudowany formularz może być przytłaczający. Tryb uproszczony jest dobrym kierunkiem, ale należy mierzyć liczbę sekcji i opcji oraz jasno pokazywać, które pola są opcjonalne i ile czasu zwykle zajmuje przejście.
- Dla dostępności trzeba zweryfikować klawiaturę i widoczny focus, semantykę przycisków/wyborów, powiązanie `label` z kontrolkami, komunikaty dla czytników ekranu i kontrast. Samo istnienie kontrolek skalowania tekstu nie zastępuje responsywnego layoutu ani WCAG.
- Kontrolki motywu i skalowania mają angielskie `aria-label` w bazowym HTML; nie należy zakładać, że dynamicznie aktualizują się przy zmianie języka. To może pogorszyć obsługę przez czytnik ekranu w interfejsie lokalnym.
- Picker używa obrazów flag z zewnętrznego `flagcdn.com`. Przy blokadzie sieci/treści obrazów może zabraknąć; flaga nie jest też dobrym jedynym oznaczeniem języka. Nazwa języka powinna być zawsze czytelna tekstowo.
- Strona opisuje prywatność jako działanie w przeglądarce, ale ładuje zewnętrzne flagi i zawiera linki do domeny internetsafer.com. Komunikat o prywatności powinien precyzyjnie rozróżnić brak wysyłania profilu od połączeń do zewnętrznych zasobów.
- Metadane SEO deklarują alternatywne adresy `hreflang` dla różnych języków, ale wszystkie prowadzą do jednego URL, podczas gdy samą lokalizację wybiera się w aplikacji. Dla rzeczywistych osobnych wersji językowych należałoby przygotować osobne adresy; jeśli ich nie ma, te alternatywy mogą być mylące.
- Komunikat awaryjny po błędzie renderowania zastępuje część aplikacji minimalnym formularzem po angielsku. To ułatwia diagnostykę, ale użytkownik może stracić kontekst, a komunikat nie wyjaśnia, co zrobić poza odświeżeniem.

## Priorytety dalszych prac

**P0 — przed publikacją:** testy funkcjonalne przeglądarkowe: wybór języka, przechodzenie wstecz/dalej, przełączanie trybu, zachowanie danych, podgląd i poprawność pobranego Markdown; sprawdzenie mobile, RTL oraz dostępności klawiaturą. Upewnić się, że w wersji produkcyjnej nie ma nieaktualnych linków ani placeholderów.

**P1 — jakość treści:** profesjonalna korekta wszystkich docelowych języków, ujednolicenie rejestru i terminologii; oznaczenie niepełnych języków i uczciwy fallback.

**P2 — utrzymanie:** rozdzielenie danych tłumaczeń od kodu, automatyczny test kompletności kluczy, lintowanie i testy UI oraz dokumentacja procesu dodawania języka.

## Etapy 1–2 — inwentaryzacja i przepływ (wykonane)

### Mapa przepływu

- Konfiguracja znajduje się w jednym HTML; aplikacja posiada tryb uproszczony (`who → start → where → truth → export`) oraz pełny (`who → start → where → style → truth → templates → tools → advanced → export`).
- Dane wejściowe są trzymane w obiekcie `state`; część jest serializowana do `localStorage` jako profil. Theme, skala tekstu i ustawienie trybu uproszczonego zapisują osobne wartości.
- Krok `export` buduje Markdown w podglądzie i udostępnia pobranie kilku formatów oraz zapis/odczyt profilu lokalnego.
- Kluczowe punkty przepływu to `renderStep`, `saveCurrent`, `refreshStepKeys`, `toggleShortMode`, `buildMarkdown` i `download*`. Dołączony kod zawiera też pozostałości starszych kluczy kroków; wymaga to dalszego porządkowania i testów.

### Problemy wykryte i poprawione

1. **Zmiana trybu mogła przenieść użytkownika na inną sekcję.** Lista kroków zmienia się zależnie od trybu, ale bieżący indeks nie zawsze oznaczał ten sam krok. Zaktualizowano odświeżanie listy: zachowuje bieżący krok po kluczu, jeśli nadal istnieje, w przeciwnym razie ogranicza indeks do dostępnego zakresu. Przełączenie zapisuje aktualny formularz i ponownie renderuje aktualny krok.
2. **Nie dało się wyczyścić wcześniej wpisanej nazwy, sloganu ani głównej reguły.** `saveCurrent()` używało operatora `||`, przez co pusty input zachowywał poprzednią wartość. Zapis teraz odzwierciedla pustą wartość, jeśli pole istnieje w DOM.
3. **Nie dało się wyczyścić przykładu dobrego tekstu w kroku stylu.** Zastosowano analogiczną poprawkę: jeśli pole istnieje, zapisywana jest dokładnie jego wartość, także pusty tekst.

### Ograniczenia sprawdzenia przepływu

Nie było dostępnego Playwrighta ani zainstalowanej przeglądarki w środowisku, dlatego nie wykonano interaktywnego testu UI. Ustalenia wynikają z przeglądu kodu i kontroli składni. Szczególnie dalszej weryfikacji wymagają ścieżki: przełączanie trybu z każdego kroku, zapis i odczyt profilu, klikanie segmentów paska postępu, pobieranie każdego formatu oraz powrót z eksportu. Zmiany nie powinny być traktowane jako pełny test funkcjonalny.

## Etapy 3–4 — eksport i przygotowanie lokalizacji (wykonane częściowo)

### Eksport — przegląd i poprawki

- Śledziłem dane od pól `state` do `buildMarkdown()`, `buildSystemPrompt()` i funkcji pobierania. Eksport zawiera warstwowe sekcje i czyta przykłady `good`/`bad`.
- Wykryto, że aktualny krok `style` renderował pole dobrych przykładów, ale nie pole antyprzykładów, mimo że generator umiał je eksportować, a README obiecywało oba typy. Dodano pole antyprzykładów z lokalizowanymi etykietami i zapis wartości przy nawigacji.
- Zmiana języka renderowała krok ponownie bez uprzedniego zapisania aktywnych pól tekstowych. Dodano zapis bieżącego kroku przed przełączeniem języka.
- Zapis profilu nie obejmował wybranego zadania zawodowego i jego strategii; dodano te pola wraz z dodatkowymi regułami roli. Wczytanie profilu przywraca teraz także jego język.
- Zasady, nagłówki warstw, testy stresowe i szablon promptu w eksporcie są w dużej mierze po angielsku nawet przy lokalnym UI. To może być celowe dla modeli, ale trzeba zdecydować i jasno pokazać, czy eksport ma być po angielsku, czy w języku interfejsu / wybranym języku pisania. W pełni nie rozwiązano tego w tym etapie.
- Funkcjonalne testy pobranych plików, parsowania Markdown i odczytu profilu w przeglądarce nadal nie zostały wykonane. Nie deklaruję więc, że eksport jest w pełni zweryfikowany.

### Przygotowanie lokalizacji

- Za źródło prawdy należy uznać kody dostępne w `LANG_FLAG_META` i aliasy `LANG_ALIASES`, a nie liczbę wpisów w słowniku bazowym `i18n`. Selektor zawiera również wariant `en-US`; to odmiana ustawienia, nie odrębny pełny pakiet tłumaczeń.
- `setLang()` klonuje pakiet bazowy (lub angielski), gdy pakiet docelowy nie istnieje, a `t()` / `L()` dokładają fallback z angielskiego. Zatem brak błędu nie oznacza kompletnej lokalizacji. Pokrycie trzeba raportować per zestaw danych (UI, flow, opcje, etykiety, komunikaty i eksport), nie tylko per język.
- Przygotowano listę problemów i kierunek audytu, ale nie przeniesiono jeszcze wszystkich słowników do jednego katalogu ani nie dodano automatycznego walidatora kompletności. To pozostaje częścią właściwego etapu lokalizacyjnego.

## Etap 5 — korekta języka polskiego (pierwsza iteracja)

Przejrzano główne teksty interfejsu, kroki kreatora, krótkie etykiety trybu, komunikaty limitów, nazwy ról i część opisu eksportu. Wprowadzono poprawki m.in.:

- usunięto niezręczne „Sprofiluj…” oraz mylące „LLM i AI”; komunikat tytułowy mówi teraz wprost o karcie stylu i modelu AI;
- zastąpiono niepotrzebne kalki „system prompt / styleguide” opisem instrukcji dla modelu;
- poprawiono „jak się z nim relacjonujesz” na „jaką relację z nim budujesz”;
- zastąpiono „CTA” polskim „wezwanie do działania” w opisie kanału;
- ujednolicono kilka terminów: „antyprzykłady”, „gotowy zestaw”, „podgląd i eksport”, „rzetelność i granice”;
- poprawiono etykiety zawodów, m.in. „Influencer / creator” na „Twórca internetowy” i „Developer / technical writer” na „Programista / autor dokumentacji technicznej”;
- poprawiono tekst trybu uproszczonego i komunikat przekroczenia limitu.

To **pierwsza iteracja korekty**, nie kompletna certyfikowana korekta wszystkich polskich opcji. Aplikacja zawiera liczne oddzielne pakiety tekstowe, presetów i opcji. Pozostałe teksty, zwłaszcza rozbudowane listy stylów i strategii, wymagają dalszego przeglądu w interfejsie. Nagłówki sześciu warstw, instrukcja systemowa, sekcje eksportu, komunikaty o źródłach i ograniczeniach oraz szablon polecenia są teraz zależne od wybranego języka interfejsu dla polskiego. Wybrane polskie opcje dotyczące wezwania do działania i marketingu oczyszczono też z części anglicyzmów. Pozostałe języki nadal używają angielskich fallbacków do czasu wykonania ich osobnych etapów. Wartość wpisana przez użytkownika pozostaje bez tłumaczenia.

## Walidacja wykonana

- `node --check` na głównym skrypcie: bez błędów składni.
- Przegląd statyczny HTML/JS oraz przykładowych wpisów tłumaczeń.
- Nie wykonano testów w prawdziwej przeglądarce, audytu kontrastu ani pełnego review językowego native speakerów; powyższe należy traktować jako audyt statyczny i listę priorytetów, nie certyfikat dostępności ani kompletnej korekty.
