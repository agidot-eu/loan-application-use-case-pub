# Proces pożyczki online dla firmy


Repozytorium zawiera kompletną dokumentację i przykłady implementacji systemu obsługującego proces udzielania pożyczek. Celem projektu jest stworzenie przejrzystego materiału edukacyjnego dla pracowników, 
który jednocześnie prezentuje przykładową architekturę opartą na mikroserwisach i REST API.
Repozytorium jest utrzymywane przez firmę AGIDOT sp. z o.o. https://agidot.eu/

## Główne Założenia Systemu

System umożliwia kompleksową obsługę wniosku o udzielenie pożyczki, dzieląc proces na kilka kluczowych etapów, z których każdy jest realizowany przez dedykowany serwis. Podejście to pozwala na łatwe skalowanie, modyfikację poszczególnych elementów oraz lepsze zrozumienie zasad działania architektury opartej na serwisach.

---

# Proces online udzielania pożyczki dla firmy

Poniżej przedstawiono poszczególne kroki procesu z informacją o wykonawcy umieszczoną w nawiasach kwadratowych przy nazwie kroku.
Szczegóły kroków są opisane w osobnych dokumentach w folderze kroki


## 1. Wstępna Rejestracja i Pozyskanie Podstawowych Danych [Klient]
- **Opis:**  
  Klient wprowadza podstawowe dane firmy, kontaktowe oraz akceptuje wymagane zgody.
- **Dane:**  
  - NIP (identyfikator firmy)  
  - Numer telefonu  
  - Adres e-mail  
  - Akceptacja regulaminu, polityki prywatności oraz zgoda na przetwarzanie danych (np. RODO).



## 2. Uzupełnienie Szczegółowych Informacji o Firmie [Klient / System]
- **Opis:**  
  System automatycznie pobiera dane z rejestrów publicznych (GUS, KRS, CEIDG) na podstawie NIP-u, a klient uzupełnia brakujące informacje dotyczące finansów oraz danych właścicieli/reprezentantów.
- **Dane:**  
  - **Automatycznie pobierane:**  
    - Nazwa firmy  
    - Forma prawna  
    - Adres siedziby  
    - Data rejestracji i status działalności  
    - Informacje o właścicielach i reprezentantach (jeśli dostępne)  
  - **Uzupełniane przez klienta:**  
    - Sprawozdania finansowe (bilans, rachunek zysków i strat)  
    - Informacje o przychodach, zyskach, bieżących zobowiązaniach  
    - Dodatkowe dokumenty potwierdzające lub uzupełniające dane


## 3. Weryfikacja Tożsamości i Autentyczności Dokumentów – Aplikanta [Aplikant]
- **Opis:**  
  Klient przesyła niezbędne dokumenty, a dedykowany aplikant (np. księgowa) weryfikuje ich autentyczność oraz zgodność z danymi pobranymi z rejestrów.
- **Etapy:**  
  - **Przesyłanie dokumentów przez klienta:**  
    Skany dokumentów rejestrowych, finansowych i dokumentów potwierdzających tożsamość.
  - **Weryfikacja przez aplikanta:**  
    Dedykowany pracownik sprawdza zgodność i autentyczność przesłanych dokumentów.


## 4. Weryfikacja Tożsamości Reprezentantów [Reprezentanci]
- **Opis:**  
  Dodatkowy proces uruchamiany niezależnie w celu potwierdzenia tożsamości osób reprezentujących firmę.  
  - **Dla JDG:** Dotyczy właściciela.  
  - **Dla spółek:** Obejmuje wszystkich reprezentantów pobranych z KRS.
- **Proces Weryfikacji Reprezentanta:**
  1. **Inicjacja:**  
     - System identyfikuje typ podmiotu i pobiera dane reprezentantów.  
     - Wysyłany jest unikalny link lub powiadomienie do reprezentantów z prośbą o weryfikację.
  2. **Przesyłanie Dokumentów:**  
     - Reprezentanci przesyłają dokumenty potwierdzające ich tożsamość (np. dowód osobisty, paszport) oraz dokumenty potwierdzające pełnienie funkcji.
  3. **Weryfikacja Tożsamości:**  
     - System porównuje przesłane dokumenty z danymi z rejestrów publicznych.  
     - Opcjonalnie stosowane są metody biometryczne (zdjęcie, wideo).
  4. **Akceptacja i Potwierdzenie:**  
     - Reprezentanci potwierdzają zgodność i autentyczność dokumentów, a wynik weryfikacji zostaje zapisany w systemie.
  5. **Powiadomienie:**  
     - Wysłanie informacji o pomyślnej weryfikacji do reprezentantów i wnioskodawcy.


## 5. Wewnętrzna Analiza Ryzyka i Ocena Zdolności Kredytowej [Dział analiz]
- **Opis:**  
  System, po uzyskaniu dodatkowych zgód, odpytuje wywiadownie kredytowe oraz wykorzystuje moduł AI do oceny zdolności kredytowej firmy.
- **Etapy:**  
  - Uzyskanie zgód na odpytanie baz (BIG, BIK, KRD, inne).  
  - Automatyczne pobranie danych z wywiadowni kredytowych.  
  - Scoring przy użyciu modułu AI.  
  - Opcjonalna analiza manualna przez zespół analityków.


## 6. Wybór Produktu [Klient / Dział ofert]
- **Opis:**  
  Po zakończeniu analizy ryzyka, klient ma możliwość wyboru jednego z 10 dostępnych produktów pożyczkowych. Oferta jest dostosowana do różnych potrzeb – kwota pożyczki, okres spłaty, sposób spłaty (np. stała rata, zmienna rata, odroczona spłata itp.).  
- **Etapy:**  
  - **Prezentacja dostępnych produktów:**  
    System wyświetla listę 10 produktów, uwzględniając różne parametry pożyczki, takie jak wysokość kwoty, sposób rat oraz dodatkowe opcje (np. odroczony termin spłaty).
  - **Personalizacja wyboru:**  
    Klient wybiera produkt odpowiadający jego potrzebom finansowym i preferowanemu modelowi spłaty.
  - **Zatwierdzenie wyboru:**  
    Wybrany produkt zostaje przypisany do dalszego procesu przygotowania oferty.


## 7. Przygotowanie Oferty Kredytowej [Dział ofert]
- **Opis:**  
  Na podstawie wyników analizy ryzyka oraz wybranego produktu generowana jest oferta kredytowa, a przygotowywany jest wstępny projekt umowy.
- **Etapy:**  
  - Ustalenie warunków pożyczki (kwota, okres spłaty, oprocentowanie, prowizje) zgodnych z wybranym produktem.  
  - Przygotowanie szkicu umowy.  
  - Weryfikacja oferty przez dział prawny i finansowy.


## 8. Zatwierdzenie Decyzji Kredytowej [Komisja Kredytowa]
- **Opis:**  
  Finalna decyzja o udzieleniu pożyczki podejmowana jest przez kierownictwo lub komisję kredytową, a wynik decyzji jest dokumentowany.
- **Etapy:**  
  - Podejmowanie decyzji na podstawie wyników analizy ryzyka oraz wybranego produktu.  
  - Dokumentacja i archiwizacja decyzji.



## 9. Prezentacja Oferty Klientowi [Pracownicy]
- **Opis:**  
  Oferta kredytowa jest przekazywana klientowi, a w razie potrzeby odbywają się negocjacje i modyfikacja warunków.
- **Etapy:**  
  - Prezentacja szczegółowej oferty wraz z warunkami.  
  - Negocjacje i akceptacja oferty przez klienta.


## 10. Finalizacja Umowy i Formalności [Klient / Pracownicy]
- **Opis:**  
  Po akceptacji oferty, umowa jest podpisywana (elektronicznie lub tradycyjnie) przez wszystkie upoważnione strony oraz archiwizowana.
- **Etapy:**  
  - Podpisanie umowy przez klienta.  
  - Weryfikacja i archiwizacja dokumentów przez dział prawny.



## 11. Wypłata Środków [Dział Płatności]
- **Opis:**  
  Po finalizacji umowy następuje realizacja przelewu ustalonej kwoty na wskazane konto firmowe oraz generowanie harmonogramu spłat.
- **Etapy:**  
  - Realizacja przelewu.  
  - Generowanie harmonogramu spłat.


## 12. Monitorowanie Spłat i Obsługa Posprzedażowa [Obsługa Klienta]
- **Opis:**  
  System monitoruje terminowość spłat, a zespół windykacyjny i obsługa klienta zapewniają wsparcie podczas trwania pożyczki.
- **Etapy:**  
  - Regularne monitorowanie spłat.  
  - Interwencje windykacyjne w razie potrzeby.  
  - Aktualizacja danych oraz generowanie raportów.
  
   

## Podsumowanie Funkcjonalności
Modularność: Każdy serwis realizuje określone zadanie, co ułatwia utrzymanie i rozwój systemu.
Przykłady Implementacji: Repozytorium zawiera przykłady zapytań i odpowiedzi dla poszczególnych punktów procesu, co ułatwia zrozumienie przepływu danych między serwisami.
Elastyczność: System przewiduje możliwość rozbudowy i modyfikacji – np. zmiana logiki oceny ryzyka czy dodanie nowych typów produktów.
Praktyczne Zastosowanie: Dokumentacja ma służyć jako materiał szkoleniowy, pokazujący zastosowanie nowoczesnych rozwiązań architektonicznych w praktyce biznesowej.
