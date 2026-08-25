# 📈 Model Prognozy ATV – Procedura Aktualizacji

Procedura opisuje kroki niezbędne do zaktualizowania danych wejściowych i wygenerowania nowej prognozy ATV na kolejny miesiąc.

---

## 1. Aktualizacja danych wejściowych
Przed uruchomieniem modelu upewnij się, że w folderze roboczym projektu znajdują się zaktualizowane pliki ze wszystkich trzech źródeł:

### A. Dane historyczne ATV
1. Pobierz najnowsze dane historyczne z systemu **TechEdge**.
   * **Ścieżka w systemie:** `Rafał Daszuta -> Time -> ATV_hourly_TSV`
2. Wyeksportuj raport do formatu `.csv`.
3. Zapisz plik w głównym folderze roboczym skryptu pod nazwą: 
   `Time ATV_hourly_TSV.csv`

### B. Baza wydarzeń (`Events`)
* Upewnij się, że plik z bazą wydarzeń jest zaktualizowany (szczególnie o wydarzenia w okresie prognozowanym).
* **Ścieżka sieciowa:** `W:\Dzial Business process\Dzial Analiz\OSOBISTE\RAFAŁ\Wewnętrzne\Events_ratings.xlsx`  
  *(Uwaga: Upewnij się, że masz aktywny dostęp do dysku W:)*

### C. Raport pogodowy
1. Przejdź do strony raportu pogodowego: **raport pogodowy - wykresy ATV**
2. Ustaw filtry: wybierz wszystkie dostępne lata, miesiące i dni w agregacji **Dziennej**.
3. Wyeksportuj wygenerowany raport do formatu `.xlsx`.
4. **Czyszczenie pliku:**
   * Usuń wykres ze skoroszytu.
   * Usuń puste wiersze na górze (nazwy kolumn tabeli **muszą** znajdować się dokładnie w pierwszym wierszu).
   * Usuń wszelkie scalenia komórek oraz puste kolumny.
5. Zapisz wyczyszczony plik w formacie `.xlsx` w folderze roboczym skryptu pod nazwą:  
   `raport pogodowy - wykresy ATV.xlsx`

---

## 2. Konfiguracja parametrów skryptu
Otwórz plik ze skryptem Python (np. `Model ATV HYBRID new.ipynb`) i przejdź do sekcji **1. Inicjalizacja i Konfiguracja Parametrów**. Zaktualizuj poniższe zmienne odpowiednio dla nowego miesiąca:

* `nazwa_pliku_prognoza` – nazwa pliku wyjściowego dla przyszłego miesiąca (np. `"ATV_prognoza_2026_10.xlsx"`)
* `last_update_date` – dzisiejsza data w formacie `YYYY-MM-DD`
* `Start_prognozowanego_miesiaca` – pierwszy dzień prognozowanego miesiąca (np. `"2026-10-01"`)
* `End_pred` – ostatni dzień prognozowanego miesiąca (np. `"2026-10-31"`)

---

## 3. Uruchomienie skryptu
1. Uruchom cały skrypt (np. opcją **Run All** w Jupyter Notebook).
2. Wynikowa średnia prognoza ATV na przyszły miesiąc zostanie wypisana w konsoli (w bloku *Eksport Danych i Ocena Jakości Modelu*).
3. Szczegółowe wyniki z predykcjami godzinowymi zostaną wyeksportowane do pliku `.xlsx` o nazwie zdefiniowanej w Kroku 2. Wygenerują się również wykresy walidacyjne.
