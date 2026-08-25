Poniższa instrukcja opisuje kroki niezbędne do zaktualizowania danych i wygenerowania nowej prognozy ATV na kolejny miesiąc.

**1. Aktualizacja danych wejściowych**
Przed uruchomieniem modelu upewnij się, że zaktualizowałeś wszystkie trzy źródła danych w folderze roboczym projektu.

**A. Dane historyczne ATV**
Pobierz najnowsze dane historyczne z systemu TechEdge.

Ścieżka w systemie: Rafał Daszuta -> Time -> ATV_hourly_TSV

Wyeksportuj raport do formatu .csv.

Zapisz plik w głównym folderze roboczym skryptu pod nazwą: Time ATV_hourly_TSV.csv.

**B. Baza wydarzeń (Events)**
Upewnij się, że plik z bazą wydarzeń jest zaktualizowany (zwłaszcza o wydarzenia w okresie prognozowanym).

Plik znajduje się pod ścieżką sieciową:
W:\Dzial Business process\Dzial Analiz\OSOBISTE\RAFAŁ\Wewnętrzne\Events_ratings.xlsx
(Uwaga: Upewnij się, że masz dostęp do dysku W:)

**C. Raport pogodowy**
Przejdź do strony raportu pogodowego: raport pogodowy - wykresy ATV

Ustaw filtry: wybierz wszystkie dostępne lata, miesiące i dni w agregacji Dziennej.

Wyeksportuj wygenerowany raport do formatu xlsx.

Czyszczenie pliku:

Usuń wykres ze skoroszytu.

Usuń puste wiersze na górze (nazwy kolumn tabeli muszą znajdować się dokładnie w pierwszym wierszu).

Usuń wszelkie scalenia komórek oraz puste kolumny.

Zapisz wyczyszczony plik w formacie .xlsx w folderze roboczym skryptu pod nazwą: raport pogodowy - wykresy ATV.xlsx.

**2. Konfiguracja parametrów skryptu**
Otwórz plik ze skryptem Python (tzw. Model ATV HYBRID new) i przejdź do sekcji 1. Inicjalizacja i Konfiguracja Parametrów. Zaktualizuj poniższe zmienne odpowiednio dla nowego miesiąca:

nazwa_pliku_prognoza – ustaw nazwę pliku wyjściowego dla przyszłego miesiąca (np. "ATV_prognoza_2026_10.xlsx").

last_update_date – ustaw na datę dzisiejszą w formacie YYYY-MM-DD.

Start_prognozowanego_miesiaca – ustaw na pierwszy dzień prognozowanego miesiąca (np. "2026-10-01").

End_pred – ustaw na ostatni dzień prognozowanego miesiąca (np. "2026-10-31").

**3. Uruchomienie skryptu**
Uruchom cały skrypt (np. opcją Run All w Jupyter Notebook).

Wynikowa średnia prognoza ATV na przyszły miesiąc zostanie wypisana w konsoli (podczas wykonywania bloku Eksport Danych i Ocena Jakości Modelu).

Szczegółowe wyniki z predykcjami godzinowymi zostaną wyeksportowane do pliku .xlsx o nazwie zdefiniowanej w kroku 2. Wygenerują się również wykresy walidacyjne.
