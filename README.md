# Podstawy_programowania_IDN
# Automatyzacja i Przetwarzanie Plików w Powłoce Bash

## Przegląd Projektu
Ten projekt to zbiór skryptów powłoki i narzędzi wiersza poleceń przeznaczonych do automatyzacji ekstrakcji tekstu, masowej konwersji obrazów oraz organizacji systemu plików. Prezentuje umiejętność przetwarzania strumieni danych, manipulacji metadanymi i strukturyzacji katalogów natywnie w środowisku UNIX/macOS, bez konieczności korzystania z zewnętrznych aplikacji graficznych.

## Architektura i Przebieg Zadań
1. **Zadanie 1 (Zespoły i narzędzia)**: Grupa: `Mikołaj Met` , `Dawid Basąg` Repozytoria github: ` https://github.com/MikolajMet` , ` https://github.com/Ponczek6969`
2. **Zadanie 2 (Instalacja dodatków)**: Instalacja brakujących pakietów (MacOS) potrzebnych do wykonania zadań. 
3. **Zadanie 3 (Niesforne dane)**: Przygotowanie pliku z danymi w jednej kolumnie do importu do arkusza kalkulacyjnego z podziałem na kolumny.
4. 
5. **Zadanie 5 (Ekstrakcja SQL do CSV)**: Wykorzystuje narzędzie `sed` z rozszerzonymi wyrażeniami regularnymi do parsowania pliku `steps-2csv.sql`. Ekstrahuje konkretne wartości liczbowe z instrukcji `INSERT`, skraca stemple czasu (zamieniając milisekundy na sekundy) i zapisuje sformatowany wynik do pliku `wynik.csv`.
6. 
7. **Zadanie 7 (Masowa Obróbka Zdjęć)**: Wykorzystuje pętlę w powłoce połączoną z natywnym dla macOS narzędziem `sips` do masowej konwersji wyodrębnionych zdjęć na format `.jpg`. Standaryzuje rozdzielczość do 96x96 DPI, skaluje wysokość do 720px i kompresuje ostateczny wynik do jednego archiwum ZIP.
8. 
9. **Zadanie 9 (Strukturyzacja Kopii Zapasowych)**: Przetwarza płaskie pliki kopii zapasowych `.zip` o nazwach w formacie `RRRR-MM-DD` rozmieszczone w różnych katalogach roboczych. Stosuje mechanizm wycinania podciągów w Bashu (`${zmienna:przesunięcie:długość}`) oraz narzędzie `basename` do dynamicznego budowania hierarchicznego drzewa katalogów `Rok/Miesiąc/` i przenosi pliki do odpowiednich lokalizacji.
10. 

## Technologie
* **Środowisko**: macOS / UNIX CLI
* **Język**: Bash
* **Przetwarzanie Tekstu**: `sed`, `dos2unix`
* **Przetwarzanie Obrazów**: `sips`
* **Zarządzanie Archiwami**: `zip`, `unzip`

## Jak Uruchomić (macOS / Linux)

1. Sklonuj repozytorium:
   ```bash
   git clone [[https://github.com/twoj-link-tutaj.git](https://github.com/twoj-link-tutaj.git)]
   cd [nazwa-katalogu]
