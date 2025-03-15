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

## 3. Weryfikacja Tożsamości i Autentyczności Dokumentów - aplikanta

- **Weryfikacja aplikanta:**  
  - **Rola aplikanta:**  
    Proces weryfikacji dokumentów i tożsamości realizowany jest przez dedykowanego aplikanta (np. księgową), która sprawdza zgodność przesłanych dokumentów z danymi pobranymi z rejestrów.
- **Weryfikacja dokumentów:**  
  - **Kontrola autentyczności:**  
    Przesłanie i weryfikacja skanów dokumentów rejestrowych, finansowych oraz dokumentów potwierdzających tożsamość osób związanych z firmą.

## 4. Weryfikacja tożsamości reprezentantów 
- **Uruchomienie dodatkowego procesu – Weryfikacja Reprezentanta:**  
  - Proces ten jest uruchamiany niezależnie w celu potwierdzenia tożsamości osób reprezentujących firmę. Dla jednoosobowej działalności gospodarczej (JDG) obejmuje weryfikację właściciela, natomiast dla spółek – wszystkich reprezentantów wskazanych w danych pobranych z KRS. Proces opisany poniżej

## 5. Wewnętrzna Analiza Ryzyka i Ocena Zdolności Kredytowej
- **Dodatkowe zgody:**
  - Uzyskanie zgód od klienta na odpytanie wywiadowni kredytowych (BIG, BIK, KRD oraz innych baz).
- **Silnik decyzyjny:**
  - Automatyczne odpytanie zewnętrznych wywiadowni kredytowych (BIG, BIK, KRD i innych) w celu uzyskania kompleksowej historii kredytowej firmy.
- **Moduł AI i scoring:**
  - Zaawansowany algorytm AI dokonuje scoringu, analizując dane finansowe, historię kredytową i inne czynniki ryzyka.
- **Analiza manualna (opcjonalnie):**
  - Weryfikacja wyników przez zespół analityków, szczególnie w przypadku nietypowych sytuacji.

## 6. Przygotowanie Oferty Kredytowej
- **Generowanie propozycji:**
  - Ustalenie warunków pożyczki – kwoty, okresu spłaty, oprocentowania, prowizji.
- **Wstępny projekt umowy:**
  - Przygotowanie szkicu umowy, który uwzględnia ustalone warunki.
- **Weryfikacja oferty wewnętrzna:**
  - Przegląd oferty przez dział prawny oraz finansowy pod kątem zgodności z regulacjami oraz polityką firmy.

## 7. Zatwierdzenie Decyzji Kredytowej
- **Decyzja kredytowa:**
  - Finalna decyzja o udzieleniu pożyczki, podejmowana przez kierownictwo lub komisję kredytową, na podstawie wyników analizy ryzyka.
- **Rejestracja decyzji:**
  - Dokumentacja wewnętrzna decyzji oraz zapis wyników analizy dla celów archiwizacji.

## 8. Prezentacja Oferty Klientowi
- **Komunikacja:**
  - Przekazanie szczegółowej oferty kredytowej wraz z warunkami pożyczki.
- **Negocjacje:**
  - W razie potrzeby negocjacje i modyfikacja warunków oferty.
- **Akceptacja oferty:**
  - Potwierdzenie warunków przez firmę pożyczkową oraz klienta.

## 9. Finalizacja Umowy i Formalności
- **Podpisanie umowy:**
  - Elektroniczne (lub tradycyjne) podpisanie umowy przez wszystkie upoważnione strony.
- **Ostateczna weryfikacja:**
  - Przegląd umowy przez dział prawny oraz finalna akceptacja warunków.
- **Archiwizacja:**
  - Zabezpieczenie i archiwizacja dokumentacji umowy.

## 10. Wypłata Środków
- **Realizacja przelewu:**
  - Przelew ustalonej kwoty na wskazane konto firmowe.
- **Harmonogram spłat:**
  - Generowanie harmonogramu spłat, udostępnianego klientowi oraz monitorowanego przez system.

## 11. Monitorowanie Spłat i Obsługa Posprzedażowa
- **Monitoring spłat:**
  - Regularne sprawdzanie terminowości spłat przez system oraz interwencje zespołu windykacyjnego, gdy zajdzie taka potrzeba.
- **Obsługa klienta:**
  - Wsparcie informacyjne i techniczne w trakcie trwania pożyczki.
- **Aktualizacja danych:**
  - Regularna aktualizacja profilu firmy oraz generowanie wewnętrznych raportów dotyczących portfela kredytowego.


---

## Proces Weryfikacji Reprezentanta

Proces ten jest dodatkowym modułem, który zapewnia, że osoby uprawnione do reprezentowania firmy są właściwie zweryfikowane i zatwierdzone. Opis poszczególnych etapów:

1. **Inicjacja Procesu:**
   - System identyfikuje typ podmiotu (JDG lub spółka) oraz pobiera dane reprezentantów z rejestrów (np. KRS, CEIDG).
   - Na tej podstawie generowany jest unikalny link lub powiadomienie, wysyłane do reprezentantów z prośbą o weryfikację.

2. **Przesyłanie Dokumentów:**
   - Reprezentanci otrzymują żądanie przesłania dokumentów potwierdzających ich tożsamość (np. dowód osobisty, paszport) oraz dokumentów potwierdzających pełnienie funkcji reprezentanta.
   - W przypadku JDG, właściciel przesyła wymagane dokumenty i zatwierdza swoją tożsamość.

3. **Weryfikacja Tożsamości:**
   - Aplikacja porównuje przesłane dokumenty z danymi pobranymi z rejestrów publicznych.
   - Opcjonalnie, wykorzystywane są metody biometryczne, takie jak weryfikacja zdjęciowa lub wideo, w celu dodatkowego potwierdzenia autentyczności.

4. **Akceptacja i Potwierdzenie:**
   - Po pozytywnej weryfikacji, reprezentanci potwierdzają swoją zgodę na warunki oraz autentyczność przesłanych dokumentów.
   - Wynik weryfikacji jest zapisywany w systemie, co umożliwia dalsze przetwarzanie wniosku o pożyczkę.

5. **Powiadomienie:**
   - Po zakończeniu procesu, zarówno reprezentanci, jak i wnioskodawca otrzymują informację o pomyślnym zakończeniu weryfikacji.
   - Weryfikacja reprezentanta jest niezbędnym warunkiem do przejścia do kolejnych etapów procesu udzielania pożyczki.
  
   

## Podsumowanie Funkcjonalności
Modularność: Każdy serwis realizuje określone zadanie, co ułatwia utrzymanie i rozwój systemu.
Przykłady Implementacji: Repozytorium zawiera przykłady zapytań i odpowiedzi dla poszczególnych punktów procesu, co ułatwia zrozumienie przepływu danych między serwisami.
Elastyczność: System przewiduje możliwość rozbudowy i modyfikacji – np. zmiana logiki oceny ryzyka czy dodanie nowych typów produktów.
Praktyczne Zastosowanie: Dokumentacja ma służyć jako materiał szkoleniowy, pokazujący zastosowanie nowoczesnych rozwiązań architektonicznych w praktyce biznesowej.
