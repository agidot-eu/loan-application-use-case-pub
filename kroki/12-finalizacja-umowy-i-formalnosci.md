# 10-finalizacja-umowy-i-formalnosci.md

```
:FinalizacjaUmowy form
Finalizacja umowy h3

Potwierdzenie danych i akceptacja warunków section
Potwierdzenie danych checkbox - Potwierdzam że wszystkie dane są poprawne
Anceptacja checkbox - Akceptuje warunki uzyskania pożyczki

Weryfikacja sms h3

Instrukcja label - Na podany numer telefonu został wysłany 4-cyfrowy kod weryfikacyjny.

KodWeryfikacyjny textbox - Wprowadź kod
Zweryfikuj kod button - Zweryfikuj kod

Wyslij ponownie kod button - Wyślij ponownie kod

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

![image](https://github.com/user-attachments/assets/b12174ea-3eb4-4874-9ae1-0d2d0a22fbc1)



Finalizacja umowy pożyczkowej to ostatni etap procesu kredytowego, w którym klient podejmuje decyzję o podpisaniu umowy na warunkach, które zostały mu zaprezentowane w ofercie. W tym kroku dochodzi do formalnego zawarcia umowy pożyczkowej pomiędzy pożyczkobiorcą a pożyczkodawcą (bankiem lub instytucją finansową). Finalizacja obejmuje m.in. potwierdzenie warunków umowy, podpisanie umowy (w formie tradycyjnej lub cyfrowej) oraz przekazanie środków na konto pożyczkobiorcy.

Poniżej przedstawiam przykładowy przebieg tego procesu oraz przykładowy model API, który może być użyty do finalizacji umowy pożyczkowej.

Proces finalizacji umowy pożyczkowej
Podsumowanie warunków oferty

Klient otrzymuje ostateczne potwierdzenie warunków pożyczki, które zostały mu wcześniej zaprezentowane w ofercie (np. kwota pożyczki, oprocentowanie, okres spłaty, miesięczna rata itp.).

Potwierdzenie, że wszystkie dane są poprawne i zgodne z oczekiwaniami klienta.

Akceptacja warunków

Klient musi zaakceptować wszystkie warunki umowy pożyczkowej.

Zwykle wiąże się to z formalnym potwierdzeniem, że klient rozumie warunki umowy i zgadza się na jej podpisanie.

Podpisanie umowy

Podpisanie tradycyjne: Klient osobiście podpisuje dokumenty umowy pożyczkowej w placówce banku lub podczas wizyty doradcy.

Podpisanie elektroniczne: W przypadku aplikacji online lub procesu zdalnego, klient podpisuje umowę przy użyciu podpisu elektronicznego (np. e-podpisu, SMS lub kodu autoryzacyjnego).

Weryfikacja i zatwierdzenie

Bank lub instytucja finansowa dokonuje weryfikacji podpisu (jeśli to wymagane) oraz sprawdza, czy wszystkie dane są poprawne.

Po zatwierdzeniu umowy, bank przekaże klientowi potwierdzenie zawarcia umowy.

Przelew środków

Po podpisaniu umowy, środki z pożyczki są przekazywane na konto bankowe klienta zgodnie z ustalonymi warunkami (np. przelew na konto klienta lub przelew gotówkowy).

Dostarczenie kopii umowy

Klient otrzymuje kopię podpisanej umowy (może to być w formie papierowej lub elektronicznej).


**1. Akceptacja warunków pożyczki**

**Parametry żądania**
{
  "user_id": "987654321",   // ID klienta
  "loan_id": "123456789",   // ID pożyczki
  "accepted_terms": true,   // Klient akceptuje warunki
  "signature_method": "digital", // Metoda podpisu (np. "digital", "sms")
  "signature": "klient_signature_code" // Cyfrowy podpis lub kod autoryzacyjny
}


**Odpowiedz:**

{
  "status": "success",
  "message": "Pożyczka została zaakceptowana. Umowa pożyczkowa została podpisana elektronicznie.",
  "contract_details": {
    "loan_amount": 10000,
    "interest_rate": 8.5,
    "loan_term": 24,
    "monthly_payment": 500,
    "total_amount_to_repay": 12000,
    "contract_date": "2025-03-31"
  }
}


Po akceptacji warunków przez klienta system potwierdza podpisanie umowy i dostarcza szczegóły umowy (kwota pożyczki, oprocentowanie, okres spłaty itp.).


**2. Dostarczenie kopii umowy**
Po finalizacji umowy klient powinien otrzymać kopię podpisanej umowy, zarówno w formie elektronicznej, jak i papierowej (w zależności od procedur banku). W przypadku umowy elektronicznej można wysłać ją na adres e-mail lub udostępnić w aplikacji mobilnej.


**Parametry żądania**

{
  "loan_id": "123456789",
  "user_id": "987654321",
  "email": "klient@example.com",    // Adres e-mail klienta
  "contract_format": "pdf"         // Format umowy (np. pdf, doc)
}


**Odpowiedz:**

{
  "status": "success",
  "message": "Kopia umowy pożyczkowej została wysłana na podany adres e-mail.",
  "contract_url": "https://bank.com/contracts/123456789.pdf"
}


