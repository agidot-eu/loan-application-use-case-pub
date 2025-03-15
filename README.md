# Proces pożyczki online dla firmy


Repozytorium zawiera kompletną dokumentację i przykłady implementacji systemu obsługującego proces udzielania pożyczek. Celem projektu jest stworzenie przejrzystego materiału edukacyjnego dla pracowników, 
który jednocześnie prezentuje przykładową architekturę opartą na mikroserwisach i REST API.
Repozytorium jest utrzymywane przez firmę AGIDOT sp. z o.o. https://agidot.eu/

## Główne Założenia Systemu
System umożliwia kompleksową obsługę wniosku o udzielenie pożyczki, dzieląc proces na kilka kluczowych etapów, z których każdy jest realizowany przez dedykowany serwis. Podejście to pozwala na łatwe skalowanie, modyfikację poszczególnych elementów oraz lepsze zrozumienie zasad działania architektury opartej na serwisach.


# Proces online udzielania pożyczki dla firmy

## 1. Wstępna Rejestracja i Pozyskanie Podstawowych Danych
- **Dane firmy:**
  - **NIP** – kluczowy identyfikator firmy, umożliwiający weryfikację w rejestrach publicznych.
- **Dane kontaktowe:**
  - Numer telefonu
  - Adres e-mail
- **Zgody i Akceptacje:**
  - Akceptacja regulaminu i polityki prywatności.
  - Zgoda na przetwarzanie danych osobowych zgodnie z obowiązującymi przepisami (np. RODO).

## 2. Uzupełnienie Szczegółowych Informacji o Firmie
- **Automatyczne pobieranie danych:**
  - **Integracja z rejestrami publicznymi:**  
    System automatycznie pobiera dane z rejestrów takich jak GUS, KRS oraz CEIDG, na podstawie podanego NIP-u. Uzupełniane są m.in.:
  - Nazwa firmy.
  - Forma prawna.
  - Adres siedziby.
  - Data rejestracji i status działalności.
  - Informacje o właścicielach i reprezentantach (jeśli dostępne).
- **Uzupełnienie danych przez klienta:**
  - **Dane finansowe:**
    - Sprawozdania finansowe (bilans, rachunek zysków i strat).
    - Informacje o przychodach, zyskach oraz bieżących zobowiązaniach.
  - **Dane właścicieli i reprezentantów:**
    - Uzupełnienie brakujących informacji, których nie udało się pozyskać automatycznie.
  - **Dodatkowe dokumenty:**
    - Załączniki potwierdzające pozyskane dane lub uzupełniające informacje.

## 3. Weryfikacja Tożsamości i Autentyczności Dokumentów
- **Weryfikacja aplikanta:**
  - **Rola aplikanta:**  
    Proces weryfikacji dokumentów i tożsamości realizowany jest przez dedykowanego aplikanta (np. księgową), która sprawdza zgodność przesłanych dokumentów z danymi pobranymi z rejestrów.
- **Weryfikacja dokumentów:**
  - **Kontrola autentyczności:**  
    Przesłanie i weryfikacja skanów dokumentów rejestrowych, finansowych oraz dokumentów potwierdzających tożsamość osób reprezentujących firmę.
- **Proces reprezentanta:**
  - **Dla JDG (jednoosobowa działalność gospodarcza):**  
    Weryfikacja i potwierdzenie tożsamości właściciela, który pełni jednocześnie funkcję reprezentanta. Proces ten jest wysyłany do właściciela w celu zatwierdzenia.
  - **Dla spółek:**  
    Weryfikacja obejmuje wszystkich reprezentantów wskazanych w danych pobranych z KRS. Każdy z reprezentantów musi potwierdzić swoją tożsamość i akceptację dokumentów, co gwarantuje pełną autoryzację.
- **Weryfikacja biometryczna (opcjonalnie):**
  - Wykorzystanie metod biometrycznych (np. zdjęcie lub wideo weryfikacyjne) w celu dodatkowego potwierdzenia tożsamości aplikanta oraz reprezentantów.

## 4. Wewnętrzna Analiza Ryzyka i Ocena Zdolności Kredytowej
- **Dodatkowe zgody:**
  - Uzyskanie zgód od klienta na odpytanie wywiadowni kredytowych (BIG, BIK, KRD oraz innych baz).
- **Silnik decyzyjny:**
  - Automatyczne odpytanie zewnętrznych wywiadowni kredytowych (BIG, BIK, KRD i innych) w celu uzyskania kompleksowej historii kredytowej firmy.
- **Moduł AI i scoring:**
  - Zaawansowany algorytm AI dokonuje scoringu, analizując dane finansowe, historię kredytową i inne czynniki ryzyka.
- **Analiza manualna (opcjonalnie):**
  - Weryfikacja wyników przez zespół analityków, szczególnie w przypadku nietypowych sytuacji.

## 5. Przygotowanie Oferty Kredytowej
- **Generowanie propozycji:**
  - Ustalenie warunków pożyczki – kwoty, okresu spłaty, oprocentowania, prowizji.
- **Wstępny projekt umowy:**
  - Przygotowanie szkicu umowy, który uwzględnia ustalone warunki.
- **Weryfikacja oferty wewnętrzna:**
  - Przegląd oferty przez dział prawny oraz finansowy pod kątem zgodności z regulacjami oraz polityką firmy.

## 6. Zatwierdzenie Decyzji Kredytowej
- **Decyzja kredytowa:**
  - Finalna decyzja o udzieleniu pożyczki, podejmowana przez kierownictwo lub komisję kredytową, na podstawie wyników analizy ryzyka.
- **Rejestracja decyzji:**
  - Dokumentacja wewnętrzna decyzji oraz zapis wyników analizy dla celów archiwizacji.

## 7. Prezentacja Oferty Klientowi
- **Komunikacja:**
  - Przekazanie szczegółowej oferty kredytowej wraz z warunkami pożyczki.
- **Negocjacje:**
  - W razie potrzeby negocjacje i modyfikacja warunków oferty.
- **Akceptacja oferty:**
  - Potwierdzenie warunków przez firmę pożyczkową oraz klienta.

## 8. Finalizacja Umowy i Formalności
- **Podpisanie umowy:**
  - Elektroniczne (lub tradycyjne) podpisanie umowy przez wszystkie upoważnione strony.
- **Ostateczna weryfikacja:**
  - Przegląd umowy przez dział prawny oraz finalna akceptacja warunków.
- **Archiwizacja:**
  - Zabezpieczenie i archiwizacja dokumentacji umowy.

## 9. Wypłata Środków
- **Realizacja przelewu:**
  - Przelew ustalonej kwoty na wskazane konto firmowe.
- **Harmonogram spłat:**
  - Generowanie harmonogramu spłat, udostępnianego klientowi oraz monitorowanego przez system.

## 10. Monitorowanie Spłat i Obsługa Posprzedażowa
- **Monitoring spłat:**
  - Regularne sprawdzanie terminowości spłat przez system oraz interwencje zespołu windykacyjnego, gdy zajdzie taka potrzeba.
- **Obsługa klienta:**
  - Wsparcie informacyjne i techniczne w trakcie trwania pożyczki.
- **Aktualizacja danych:**
  - Regularna aktualizacja profilu firmy oraz generowanie wewnętrznych raportów dotyczących portfela kredytowego.


## Podsumowanie Funkcjonalności
Modularność: Każdy serwis realizuje określone zadanie, co ułatwia utrzymanie i rozwój systemu.
Przykłady Implementacji: Repozytorium zawiera przykłady zapytań i odpowiedzi dla poszczególnych punktów procesu, co ułatwia zrozumienie przepływu danych między serwisami.
Elastyczność: System przewiduje możliwość rozbudowy i modyfikacji – np. zmiana logiki oceny ryzyka czy dodanie nowych typów produktów.
Praktyczne Zastosowanie: Dokumentacja ma służyć jako materiał szkoleniowy, pokazujący zastosowanie nowoczesnych rozwiązań architektonicznych w praktyce biznesowej.
