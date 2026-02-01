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

## Wymagania opcjonalne ✨
- Losowe, wymienne komunikaty dla podpowiedzi (zamiast jednego stałego tekstu)
- Ekran wyników z możliwością przełączania widoku TOP5 wg poziomu trudności
- Tryb zakładu: po wybraniu poziomu gra pyta, czy gracz chce ograniczyć maksymalną liczbę prób (jeśli tak — podaje limit)

---

## Obsługa
1. Sterowanie wykonane jest za pomoca cyfr i znaków z klawiatury
2. Po uruchomieniu widzimy ekran powitalny z opcjami: nowa gra, TOP5, wyjście
3. Po wybraniu nowej gry można wybrać poziom i (opcjonalnie) tryb zakładu
4. W trakcie gry: liczba prób rośnie, a po każdej nieudanej próbie wyświetlana jest losowa wskazówka (za mała/za duża)
5. Po trafieniu program prosi o imię, zapisuje wynik w pliku i wraca do ekranu powitalnego
6. Ekran TOP5 pokazuje maksymalnie 5 najlepszych wyników dla wybranego poziomu, posortowane rosnąco po liczbie prób
7. Program obsługuje brak pliku wyników (tworzy nowy) oraz błędy parsowania (np. przywrócenie domyślnej struktury)
