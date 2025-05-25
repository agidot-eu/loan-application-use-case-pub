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




## 2. Weryfikacja e-mail [Klient]
- **Opis:**  
  Po podaniu adresu e-mail klient otrzymuje wiadomość e-mail z 4-cyfrowym kodem, który musi wpisać w systemie.  

## 3. Weryfikacja SMS [Klient]
- **Opis:**  
  Po podaniu numeru telefonu klient otrzymuje wiadomość SMS z 4-cyfrowym kodem, który musi wprowadzić w systemie, aby przejść dalej.  

## 4. Uzupełnienie Szczegółowych Informacji o Firmie [Klient / System]
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


## 5. Weryfikacja Tożsamości i Autentyczności Dokumentów – Aplikanta [Aplikant]
- **Opis:**  
  Klient przesyła niezbędne dokumenty, a dedykowany aplikant (np. księgowa) weryfikuje ich autentyczność oraz zgodność z danymi pobranymi z rejestrów.
  Sprawdzanie odbywa się na podstawie odpytanie serwisu BIK
- **Dane:**  
  - PESEL  
  - Numer i seria dowodu
  - Data ważności dowodu
  

## 6. Weryfikacja Tożsamości Reprezentantów [Reprezentanci]
- **Opis:**  
  Dodatkowy proces uruchamiany niezależnie w celu potwierdzenia tożsamości osób reprezentujących firmę.  
  - **Dla JDG:** Dotyczy właściciela.  
  - **Dla spółek:** Obejmuje wszystkich reprezentantów pobranych z KRS.
- **Proces Weryfikacji Reprezentanta:**
  1. **Inicjacja:**  
     - System identyfikuje typ podmiotu i pobiera dane reprezentantów.  
     - Wysyłany jest unikalny link lub powiadomienie do reprezentantów z prośbą o weryfikację.
  2. - **Dane:**  
      - PESEL  
      - Numer i seria dowodu
      - Data ważności dowodu
  3. **Weryfikacja Tożsamości:**  
     - System porównuje przesłane dokumenty z danymi z rejestrów publicznych.  
     - Opcjonalnie stosowane są metody biometryczne (zdjęcie, wideo).
  4. **Akceptacja i Potwierdzenie:**  
     - Reprezentanci potwierdzają zgodność i autentyczność dokumentów, a wynik weryfikacji zostaje zapisany w systemie.
  5. **Powiadomienie:**  
     - Wysłanie informacji o pomyślnej weryfikacji do reprezentantów i wnioskodawcy.


## 7. Wewnętrzna Analiza Ryzyka i Ocena Zdolności Kredytowej [Dział analiz]
- **Opis:**  
  System, po uzyskaniu dodatkowych zgód, odpytuje wywiadownie kredytowe oraz wykorzystuje moduł AI do oceny zdolności kredytowej firmy.
- **Etapy:**  
  - Uzyskanie zgód na odpytanie baz (BIG, BIK, KRD, inne).  
  - Automatyczne pobranie danych z wywiadowni kredytowych.  
  - Scoring przy użyciu modułu AI.  
  - Opcjonalna analiza manualna przez zespół analityków.


## 8. Wybór Produktu [Klient / Dział ofert]
- **Opis:**  
  Po zakończeniu analizy ryzyka, klient ma możliwość wyboru jednego z 10 dostępnych produktów pożyczkowych. Oferta jest dostosowana do różnych potrzeb – kwota pożyczki, okres spłaty, sposób spłaty (np. stała rata, zmienna rata, odroczona spłata itp.).  
- **Etapy:**  
  - **Prezentacja dostępnych produktów:**  
    System wyświetla listę 10 produktów, uwzględniając różne parametry pożyczki, takie jak wysokość kwoty, sposób rat oraz dodatkowe opcje (np. odroczony termin spłaty).
  - **Personalizacja wyboru:**  
    Klient wybiera produkt odpowiadający jego potrzebom finansowym i preferowanemu modelowi spłaty.
  - **Zatwierdzenie wyboru:**  
    Wybrany produkt zostaje przypisany do dalszego procesu przygotowania oferty.


## 9. Przygotowanie Oferty Kredytowej [Dział ofert]
- **Opis:**  
  Na podstawie wyników analizy ryzyka oraz wybranego produktu generowana jest oferta kredytowa, a przygotowywany jest wstępny projekt umowy.
- **Etapy:**  
  - Ustalenie warunków pożyczki (kwota, okres spłaty, oprocentowanie, prowizje) zgodnych z wybranym produktem.  
  - Przygotowanie szkicu umowy.  
  - Weryfikacja oferty przez dział prawny i finansowy.


## 10. Zatwierdzenie Decyzji Kredytowej [Komisja Kredytowa]
- **Opis:**  
  Finalna decyzja o udzieleniu pożyczki podejmowana jest przez kierownictwo lub komisję kredytową, a wynik decyzji jest dokumentowany.
- **Etapy:**  
  - Podejmowanie decyzji na podstawie wyników analizy ryzyka oraz wybranego produktu.  
  - Dokumentacja i archiwizacja decyzji.



## 11. Prezentacja Oferty Klientowi [Pracownicy]
- **Opis:**  
  Oferta kredytowa jest przekazywana klientowi, a w razie potrzeby odbywają się negocjacje i modyfikacja warunków.
- **Etapy:**  
  - Prezentacja szczegółowej oferty wraz z warunkami.  
  - Negocjacje i akceptacja oferty przez klienta.


## 12. Finalizacja Umowy i Formalności [Klient / Pracownicy]
- **Opis:**  
  Po akceptacji oferty, umowa jest podpisywana (elektronicznie lub tradycyjnie) przez wszystkie upoważnione strony oraz archiwizowana.
- **Etapy:**  
  - Podpisanie umowy przez klienta.  
  - Weryfikacja i archiwizacja dokumentów przez dział prawny.



## 13. Wypłata Środków [Dział Płatności]
- **Opis:**  
  Po finalizacji umowy następuje realizacja przelewu ustalonej kwoty na wskazane konto firmowe oraz generowanie harmonogramu spłat.
- **Etapy:**  
  - Realizacja przelewu.  
  - Generowanie harmonogramu spłat.


## 14. Monitorowanie Spłat i Obsługa Posprzedażowa [Obsługa Klienta]
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

## Widok procesu
1. ![image](https://github.com/user-attachments/assets/348a8141-52ba-4bcb-b27b-7564fbefeae6)
2. ![image](https://github.com/user-attachments/assets/ca8ac36c-42b5-45a7-a738-ef8ad217e874)
3. ![image](https://github.com/user-attachments/assets/544cec0a-283b-4c75-9c7a-e8a30a52cdf8)


# Szablon

```
:PozyczkaOnline form
Pożyczka online h3

DaneFirmy section
 Dane firmy h5
 Nip textbox
 NumerTelefonu textbox
 AdresEmail textbox

Zgody section
 Zgody h5

PodstawoweZgody formfield
 Podstawowe zgody label
 regulamin checkbox - Akceptacja regulaminu i polityki prywatności.
 przetwazanie checkbox - Zgoda na przetwarzanie danych osobowych zgodnie z obowiązującymi przepisami (np. RODO).

ZgodyMarketingowe formfield
 Zgody marketingowe label
 ZgodaTelefon checkbox - Wyrażam zgodę na kontakt telefoniczny w celu przedstawienia mi oferty produktów pożyczkowych firmy XYZ.
 ZgodaSMS checkbox - Wyrażam zgodę na otrzymywanie wiadomości SMS z informacjami o promocjach, ofertach specjalnych oraz nowościach produktów.
 ZgodaEmail checkbox -Wyrażam zgodę na otrzymywanie wiadomości e-mail zawierających informacje o produktach, aktualnościach oraz ofertach marketingowych.

Header header
 LogoFirmy img datasource="https://structura.agidot.eu/api/upload-image/get/image-13.png"
 g1
 Rejestracja link 
 DaneFinansowe link
 Realizacja link

Sidebar sidebar
 column
  LogoFirmy img datasource="https://structura.agidot.eu/api/upload-image/get/image-13.png"
  NazwaFirmy label
  g2
 panelmenu
  Analiza panelmenuitem
  Klienci panelmenuitem
 column
  g3 
  www.agidot.eu label
  Copyright Ⓒ 2025 label


```
