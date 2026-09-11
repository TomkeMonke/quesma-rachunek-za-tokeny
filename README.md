# Rachunek za tokeny

Frontend dla raportu o ekonomii tokenów w sesjach agentów kodujących. Cały dokument jest zaprojektowany jako jeden paragon z drukarki termicznej: rolka papieru na ciemnym blacie, pozycje z kropkami wiodącymi, nadruk dot-matrix na słupkach, perforacje między sekcjami, pieczątka i kod kreskowy na końcu.

**Podgląd:** otwórz `index.html` w przeglądarce. Strona jest w pełni samodzielna, bez zależności i bez połączeń sieciowych.

## Co zawiera

Dwa dokumenty źródłowe złożone w jedną rolkę:

- `source/FINDINGS.md` - pełny raport: 24 tezy warstwy 1, sondy warstwy 1b, klasyfikacja promptów, werdykty sędziego, syntezy krzyżowe, zastrzeżenia, rekomendacje
- `source/SIX_THESES.md` - sześć tez z pełnymi definicjami operacyjnymi i tabelami

Zbiór: SWE-chat enhanced 2026-07-05, 9 770 sesji, 17,8 GB transkryptów, 344 repozytoria, harnessy Claude Code, Codex, OpenCode i Cursor. Łączny koszt populacji: 116 677 USD, rozłożony na pojedyncze wywołanie API i pojedynczy wynik narzędzia.

## Sekcje

| Kotwica | Zawartość |
|---|---|
| `#suma` | T01, struktura kosztu i pasek składników |
| `#pozycje` | dziesięć ustaleń jako pozycje paragonu |
| `#czynsz` | T04, czynsz za kontekst plus werdykt sędziego |
| `#kawa` | T02, pękanie cache po przerwie, narzędzie edycji, narzut JSON |
| `#tryby` | tryby kodowania, T15, T12 |
| `#ludzie` | warstwa 2, co ludzie piszą i co za to płacą |
| `#sondy` | warstwa 1b, sondy na surowych plikach |
| `#szesc` | sześć tez z tabelami |
| `#metoda` | cztery warstwy, cennik, pułapki w danych, zastrzeżenia |
| `#zalecenia` | rekomendacje i tabela „kto decyduje” |

## Design

Warstwa wizualna jest zbudowana na systemie ze strony **quesma.com**: ciepła bibuła zamiast białego tła, rdza jako jedyny akcent, zero zaokrągleń, hairline'owe ramki, liczby zawsze monospace. Stąd wzięty jest też dobór krojów.

- **Schibsted Grotesk** - logotyp i duże liczby
- **Fragment Mono** - cała reszta: pozycje, tabele, etykiety, osie

Oba kroje są na licencji SIL OFL 1.1 i leżą wbudowane w `fonts.css` jako `data:` URI (podzbiory latin + latin-ext, bo tekst jest po polsku). Strona nie wychodzi do żadnego CDN-u.

### Paleta

| Token | Jasny | Ciemny |
|---|---|---|
| `--counter` blat | `#171411` | `#080706` |
| `--paper` rolka | `#FBF9F4` | `#191511` |
| `--ink` tusz | `#1A1611` | `#EDE6D9` |
| `--rust` akcent | `#B9523C` | `#E08462` |
| `--highlight` zakreślacz | `#EEDD9C` | `#4A3D18` |
| `--s1..--s4` gęstość nadruku | `#7D3529` → `#E8CCC2` | `#F0A88E` → `#5C3226` |

Oba motywy są zaprojektowane osobno, nie odwrócone. Motyw idzie za ustawieniem systemu (`prefers-color-scheme`), a przycisk **TUSZ** w listwie kasy nadpisuje go przez `data-theme` na `<html>`.

### Wykresy

Jedna rodzina: słupek o wysokości 11-12 px z nadrukiem dot-matrix (`repeating-linear-gradient`, 2 px nadruku na 1 px przerwy) na nienadrukowanym torze. Trzy gęstości: `--rust` dla pozycji wyróżnionej, `--rust-deep` dla reszty, `--ink-3` dla tła porównania. Wszystkie liczby na `tabular-nums`, wszystkie wartości podpisane wprost, każda duża tabela ma swój odpowiednik tekstowy pod wykresem. Waffle 25 × 8 to 200 komórek, jedna komórka to pół punktu procentowego.

## Dostępność i zachowanie

- pełna obsługa `prefers-reduced-motion`: słupki pojawiają się od razu, kursor kasy przestaje mrugać
- `:focus-visible` na wszystkim, co klikalne, plus link „przejdź do treści”
- szerokie tabele scrollują się we własnym kontenerze, `body` nigdy nie jedzie w bok
- identyfikacja serii nigdy nie idzie samym kolorem: każda pozycja ma etykietę i wartość
- zero zależności, zero requestów, jeden plik HTML plus jeden CSS z krojami

## Licencje

Kroje: Schibsted Grotesk i Fragment Mono, SIL Open Font License 1.1.
