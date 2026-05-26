# Podstawy_programowania_IDN
# Automatyzacja i Przetwarzanie Plików w Powłoce Bash

## Przegląd Projektu
Ten projekt to zbiór skryptów powłoki i narzędzi wiersza poleceń przeznaczonych do automatyzacji ekstrakcji tekstu, masowej konwersji obrazów oraz organizacji systemu plików. Prezentuje umiejętność przetwarzania strumieni danych, manipulacji metadanymi i strukturyzacji katalogów natywnie w środowisku UNIX/macOS, bez konieczności korzystania z zewnętrznych aplikacji graficznych.

## Architektura i Przebieg Zadań
1. **Zadanie 1 (Zespoły i narzędzia)**: Grupa: `Mikołaj Met` , `Dawid Basąg` Repozytoria github: ` https://github.com/MikolajMet` , ` https://github.com/Ponczek6969`
2. **Zadanie 2 (Instalacja dodatków)**: Instalacja brakujących pakietów (MacOS) potrzebnych do wykonania zadań. 
3. **Zadanie 3 (Niesforne dane)**: Na podstawie danych z pliku `dane.txt` tworzy nowy plik nadający się do importu do arkusza kalkulacyjnego z podziałem na kolumny.
4. **Zadanie 4 (Dodawanie poprawek)**: Wykorzystuje narzędzie `diff` do wygenerowania łatki (`latka.patch`) z różnicami między plikami, a następnie nakłada ją na oryginalną listę przy użyciu polecenia `patch`. Poprawność operacji i zgodność plików jest na koniec weryfikowana poprzez porównanie ich sum kontrolnych za pomocą `md5sum`.
5. **Zadanie 5 (Z SQL do CSV i z powrotem)**: Zadanie składa się z dwóch etapów. Pierwszy polega na odczytaniu danych z pliku `steps-2sql.csv` i wygenerowaniu na ich podstawie zapytań do bazy danych (`INSERT INTO`). Drugi etap to operacja w odwrotną stronę – skrypt odczytuje gotowy plik `steps-2csv.sql`, wyciąga z niego z powrotem same wartości liczbowe do formatu CSV i przy okazji skraca stemple czasu (zamienia milisekundy na sekundy) przy użyciu narzędzia `sed`. 
6. **Zadanie 6 (Marudny tłumacz)** Wykorzystuje narzędzia `sed` oraz `grep` do zautomatyzowanego formatowania plików tłumaczeń w formacie JSON5. Skrypt dubluje i komentuje istniejące linie z kluczami, a także porównuje pliki i odfiltrowuje nowe frazy z nowszej wersji oprogramowania, tworząc gotowe do pracy szablony dla tłumacza.
7. **Zadanie 7 (Fotografik Gamoń)**: Wykorzystuje pętlę połączoną z natywnym dla macOS narzędziem `sips` do masowej konwersji wyodrębnionych zdjęć z plików `kopie-1` i `kopie-2` na format `.jpg`. Zmienia rozdzielczość na 96x96 DPI, skaluje wysokość do 720px i kompresuje ostateczny wynik do archiwum ZIP.
8. **Zadanie 8 (Wszędzie te PDF-y):** Wykorzystuje skrypt napisany w języku Python (z użyciem biblioteki `fpdf2`) do zautomatyzowanego wygenerowania dokumentu PDF. Skrypt zaczytuje z folderu wszystkie gotowe zdjęcia `.jpg`, dzieli je na porcje po 8 sztuk i układa na stronach formatu A4 w idealnej siatce (2 kolumny, 4 wiersze). Zabezpiecza proporcje obrazów, centralnie wyrównuje ich podpisy oraz wyłącza domyślne marginesy stron.
9. **Zadanie 9 (Porządki w kopiach zapasowych)**: Rozwiązuje problem bałaganu z plikami ZIP wrzuconymi zbiorczo do folderów `kopie-1` i `kopie-2`. Skrypt analizuje nazwę każdego pliku (zapisaną w formacie RRRR-MM-DD.zip), wycina z niej konkretny rok i miesiąc, po czym automatycznie tworzy odpowiednie podkatalogi (w formacie `Rok/Miesiąc/`) i segreguje tam poszczególne archiwa.
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
   git clone https://github.com/MikolajMet/Podstawy_programowania_IDN
   cd Podstawy_programowania_IDN
   ```

2. Instalacja dodatków MacOS:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   brew install imagemagick dos2unix diffutils
   ```
   Gdyby nie działało:
   ```bash
   export PATH="/opt/homebrew/bin:/usr/local/bin:$PATH"
   brew install imagemagick dos2unix diffutils
   ```

3. Niesforne dane:
   ```bash
   #Konwersja danych do formatu MacOS:
   dos2unix dane.txt
   #Podzielenie danych na 3 kolumny z nagłówkami:
   (printf "x\ny\nz\n"; cat dane.txt) | paste - - - | column -t > dane_wynik.txt
   ```

4. Dodawanie poprawek:
   ```bash
   #Krok 1:
   diff -u lista.txt lista-pop.txt > latka.patch
   #Krok 2:
   patch lista.txt < latka.patch
   #Krok 3:
   md5sum lista.txt
   md5sum lista-pop.txt
   ```

5. Z CVS do SQL i z powrotem:
   ```bash
   #Krok1 CSV na SQL
   cd csv
   dos2unix steps-2sql.csv
   awk -F';' 'NR>1 {printf "INSERT INTO stepsData (time, intensity, steps) VALUES (%s, %s, %s);\n", $1, $2, $3}' steps-2sql.csv > gotowy_sql.sql

   #Krok2 SQL na CSV
   dos2unix steps-2csv.sql
   echo "dateTime; steps; synced" > kroki.csv
   sed -E -n 's/.*VALUES \(([0-9]+)000, *([0-9]+), *([0-9]+)\);/\1;\2;\3/p' steps-2csv.sql >> kroki.csv
   ```

6. Mrudny tłumacz:
   ```bash
   #Krok 1:
   sed -E 's/^([ \t]*".*":.*)/\/\/ \1\n\1\n/' en-7.2.json5 > pl-7.2.json5

   #Krok 2:
   echo "{" > pl-7.4.json5
   grep -vxFf en-7.2.json5 en-7.4.json5 | grep '":' | sed -E 's/^([ \t]*".*":.*)/\/\/ \1\n\1\n/' >> pl-7.4.json5
   echo "}" >> pl-7.4.json5
   ```

7. Fotografik gamoń:
   ```bash
   #Stworzenie nowego folderu do wypakowania plików:
   mkdir niesk
   for plik in kopie-1/*.zip kopie-2/*.zip; do unzip -j "$plik" -d niesk; done
   #Stworzenie finalnego folderu z plikami ze zmienionym formatem i rozdzielczością:
   mkdir -p GotoweZdjecia
   for plik in *.*; do if [ -f "$plik" ]; then sips -s format jpeg -s dpiWidth 96.0 -s dpiHeight 96.0 --resampleHeight 720 "$plik" --out "GotoweZdjecia/${plik%.*}.jpg" 2>/dev/null; fi; done
   #Usunięcie plików z niechcianym formatem:
   cd GotoweZdjecia
   rm *.png *.PNG *.gif *.GIF 2>/dev/null
   #Spakowanie do archiwum
   zip -r ../Zadanie7_Fotografik_Gotowe.zip *
   ```

8. Wszędzie te PDF-y:
   ```bash
   # Krok 1: Instalacja niezbędnej biblioteki w terminalu
   pip install fpdf2
   # Krok 2: skrypt w języku python
   from fpdf import FPDF
   import glob
   import os

   zdjecia = sorted(glob.glob("*.jpg"))

   pdf = FPDF(format='A4')
   pdf.set_auto_page_break(auto=False, margin=0)
   pdf.set_font("helvetica", size=9)

   for i, plik in enumerate(zdjecia):
       if i % 8 == 0:
           pdf.add_page()
    
       pozycja = i % 8

       x = 20 + (pozycja % 2) * 95
       y = 15 + (pozycja // 2) * 68

       pdf.image(plik, x=x, y=y, w=80, h=55, keep_aspect_ratio=True)

       pdf.set_xy(x, y + 56)
       pdf.cell(80, 5, txt=os.path.basename(plik), align="C")

   pdf.output("portfolio.pdf")
   print("PDF został wygenerowany jako 'portfolio.pdf'")
   ```

9. Porządki w  kopiach zapsowych:
    ```bash
    #Stworzenie nowego folderu
    mkdir -p uporzadkowane
    #Porządkowanie plików z podziałem rok/miesiąc
    for plik in kopie-1/*.zip kopie-2/*.zip; do if [ -f "$plik" ]; then nazwa=$(basename "$plik"); rok=${nazwa:0:4}; miesiac=${nazwa:5:2}; mkdir -p "uporzadkowane/$rok/$miesiac"; mv "$plik" "uporzadkowane/$rok/$miesiac/"; fi; done
    #Usunięcie starych plików
    rm -rf kopie-1 kopie-2
    ```

10. Galeria dla grafika:
    ```bash

    ```

