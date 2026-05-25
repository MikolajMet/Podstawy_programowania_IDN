# Podstawy_programowania_IDN
# Automatyzacja i Przetwarzanie Plików w Powłoce Bash

## Przegląd Projektu
Ten projekt to zbiór skryptów powłoki i narzędzi wiersza poleceń przeznaczonych do automatyzacji ekstrakcji tekstu, masowej konwersji obrazów oraz organizacji systemu plików. Prezentuje umiejętność przetwarzania strumieni danych, manipulacji metadanymi i strukturyzacji katalogów natywnie w środowisku UNIX/macOS, bez konieczności korzystania z zewnętrznych aplikacji graficznych.

## Architektura i Przebieg Zadań
1. **Zadanie 1 (Zespoły i narzędzia)**: Grupa: `Mikołaj Met` , `Dawid Basąg` Repozytoria github: ` https://github.com/MikolajMet` , ` https://github.com/Ponczek6969`
2. **Zadanie 2 (Instalacja dodatków)**: Instalacja brakujących pakietów (MacOS) potrzebnych do wykonania zadań. 
3. **Zadanie 3 (Niesforne dane)**: Tworzy plik nadający się do importu do arkusza kalkulacyjnego z podziałem na kolumny.
4. 
5. **Zadanie 5 (Z SQL do CSV i z powrotem)**: Zadanie składa się z dwóch etapów. Pierwszy polega na odczytaniu danych z pliku CSV i automatycznym wygenerowaniu na ich podstawie zapytań do bazy danych (`INSERT INTO`). Drugi etap to operacja w odwrotną stronę – skrypt odczytuje gotowy plik SQL (`steps-2csv.sql`), wyciąga z niego z powrotem same wartości liczbowe do formatu CSV i przy okazji skraca stemple czasu (zamienia milisekundy na sekundy) przy użyciu narzędzia `sed`. 
6. 
7. **Zadanie 7 (Fotografik Gamoń)**: Wykorzystuje pętlę połączoną z natywnym dla macOS narzędziem `sips` do masowej konwersji wyodrębnionych zdjęć na format `.jpg`. Zmienia rozdzielczość na 96x96 DPI, skaluje wysokość do 720px i kompresuje ostateczny wynik do archiwum ZIP.
8. 
9. **Zadanie 9 (Porządki w kopiach zapasowych)**: Rozwiązuje problem bałaganu z plikami ZIP wrzuconymi zbiorczo do folderów. Skrypt analizuje nazwę każdego pliku (zapisaną w formacie RRRR-MM-DD.zip), wycina z niej konkretny rok i miesiąc, po czym automatycznie tworzy odpowiednie podkatalogi (w formacie `Rok/Miesiąc/`) i segreguje tam poszczególne archiwa.
10. 

## Technologie
* **Środowisko**: macOS / UNIX CLI
* **Język**: Bash
* **Przetwarzanie Tekstu**: `sed`, `dos2unix`
* **Przetwarzanie Obrazów**: `sips`
* **Zarządzanie Archiwami**: `zip`, `unzip`

## Jak Uruchomić 

1. Sklonuj repozytorium:
   ```bash
   git clone [[https://github.com/MikolajMet/Podstawy_programowania_IDN](https://github.com/MikolajMet/Podstawy_programowania_IDN)]
   cd [nazwa-katalogu]
   ```

2. Instalacja dodatków MacOS
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   brew install imagemagick dos2unix diffutils
   ```
   Gdyby nie działało
   ```bash
   export PATH="/opt/homebrew/bin:/usr/local/bin:$PATH"
   brew install imagemagick dos2unix diffutils
   ```

3. Niesforne dane (MacOS)
   ```bash
   dos2unix dane.txt
   (printf "x\ny\nz\n"; cat dane.txt) | paste - - - | column -t > dane_wynik.txt
   ```

4. Dodawanie poprawek
   ```bash
   
   ```

5. Z CVS do SQL i z powrotem
   ```bash

   ```

6. Mrudny tłumacz
   ```bash

   ```

7. Fotografik gamoń
   ```bash

   ```

8. Wszędzie te PDF-y
   ```bash

   ```

9. Porządki w  kopiach zapsowych
    ```bash

    ```

10. Galeria dla grafika
    ```bash

    ```

