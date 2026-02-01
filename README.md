# "Zgadnij liczbę" — specyfikacja projektu (C++)

## Krótkie streszczenie
Prosty tekstowy program "Zgadnij liczbę" napisany w C++. Gracz wybiera poziom trudności, a program losuje liczbę z odpowiedniego zakresu. Gracz zgaduje aż trafi, a po trafieniu podaje swoje imię i — w razie wejścia do TOP5 — wynik jest zapisywany.

---

## Wymagania obowiązkowe ✅
- **Ekran powitalny** z wyborem:
  - rozpocznij nową grę
  - sprawdź aktualne **TOP5** (wyświetlane tylko gdy istnieją wyniki)
- **Wybór poziomu trudności** (przykładowe zakresy):
  - łatwy: 1–50
  - średni: 1–100
  - trudny: 1–250
- **Podczas gry** zawsze widoczny jest numer aktualnej próby (liczba podejść)
- Przy nieprawidłowej próbie program informuje, czy podana liczba jest **za mała** czy **za duża**, i zwiększa licznik prób
- Przy trafieniu: program prosi o podanie imienia i wraca do ekranu powitalnego
- **Zapis wyników do pliku** i ich wczytywanie przy starcie programu (zapewnienie, że plik jest bezpiecznie parsowany i obsługa błędów)

## Wymagania opcjonalne (nice to have) ✨
- Losowe, wymienne komunikaty dla podpowiedzi (zamiast jednego stałego tekstu)
- Ekran wyników z możliwością przełączania widoku TOP5 wg poziomu trudności
- Tryb zakładu: po wybraniu poziomu gra pyta, czy gracz chce ograniczyć maksymalną liczbę prób (jeśli tak — podaje limit)

---

## Kryteria akceptacji (testy manualne / automatyczne) 🧪
1. Program kompiluje się poleceniem (przykład):

   ```bash
   g++ -std=c++17 -O2 -Wall main.cpp -o zgadnij.exe
   ./zgadnij.exe
   ```

2. Po uruchomieniu widzimy ekran powitalny z opcjami: nowa gra, TOP5, wyjście
3. Po wybraniu nowej gry można wybrać poziom i (opcjonalnie) tryb zakładu
4. W trakcie gry: liczba prób rośnie, a po każdej nieudanej próbie wyświetlana jest wskazówka (za mała/za duża)
5. Po trafieniu program prosi o imię, zapisuje wynik w pliku i wraca do ekranu powitalnego
6. Ekran TOP5 pokazuje maksymalnie 5 najlepszych wyników dla wybranego poziomu, posortowane rosnąco po liczbie prób
7. Program obsługuje brak pliku wyników (tworzy nowy) oraz błędy parsowania (np. przywrócenie domyślnej struktury)

---

## Format zapisu TOP5 (proponowany) 💾
Plik: `scores.json` (lub `top5.json`) — przykładowa struktura:

```json
{
  "easy": [ {"name":"Ala","attempts":3,"date":"2026-02-01"} ],
  "medium": [],
  "hard": []
}
```
- Dla każdego poziomu przechowujemy listę wyników: `name`, `attempts`, `date` oraz opcjonalnie `maxAttempts` gdy użyto trybu zakładu
- Po zapisaniu nowego wyniku lista jest sortowana po `attempts`, a następnie obcinana do 5 elementów

---

## Wskazówki implementacyjne 🔧
- Użyć standardowych bibliotek C++: <random> dla losowania, <fstream> / <nlohmann/json> (jeśli dopuszczalne) lub własny prosty parser do zapisu/odczytu JSON
- Zaimplementować warstwę odpowiedzialną za I/O wyników (funkcje: loadScores, saveScores, addScore)
- Przygotować listę komunikatów (const vector<string>) i losować z niej teksty pomocnicze
- Zapewnić testy manualne dla scenariuszy: brak pliku, pełny plik, wpis do TOP5 i poza TOP5

---

## Dodatkowe wymagania organizacyjne ✅
- Użycie Gita do wersjonowania i opisania pracy (czytelne commity: np. `feat: add score saving`, `fix: handle corrupt scores file`)
- Krótkie README z instrukcją budowania i uruchamiania programu

---

## Kryterium oceny (sugestia dla prowadzącego) ⭐
- Funkcjonalność: 60% (kompilacja, poprawne działanie, zapis/wczytanie TOP5)
- Jakość kodu: 20% (czytelność, modularność, obsługa błędów)
- Dodatki: 20% (losowe komunikaty, tryb zakładu, wygodny interfejs)


---

*W razie potrzeby mogę dopracować plik: dodać przykładowe diagramy przepływu gry, szczegółową listę testów lub gotowy szablon pliku `scores.json`.*
