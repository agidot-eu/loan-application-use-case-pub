# 2. Uzupełnienie Szczegółowych Informacji o Firmie [Klient / System]

## Opis
Na tym etapie system automatycznie pobiera podstawowe dane firmy z rejestrów publicznych na podstawie numeru NIP, a klient uzupełnia brakujące informacje dotyczące kondycji finansowej oraz struktury właścicielskiej. Proces ten minimalizuje wysiłek klienta i redukuje błędy, dzięki czemu dane są spójne i aktualne.

Dane pobierane automatycznie oraz te wprowadzane ręcznie podlegają walidacji, a ich kompletność jest kluczowa dla dalszych etapów procesu pożyczkowego.

---

## Dane Pobierane Automatycznie
System integruje się z rejestrami publicznymi (np. GUS, KRS, CEIDG) i pobiera następujące informacje:

- **Identyfikacja firmy:**
  - NIP
  - REGON
  - Nazwa firmy
  - Forma prawna
  - Status działalności
  - Data rejestracji
  - Kody PKD

- **Adresy:**
  - Adres siedziby
  - Adres do korespondencji (jeśli inny niż siedziby)

- **Informacje o właścicielach i reprezentantach:**
  - Imię i nazwisko / Nazwa podmiotu
  - PESEL (jeśli dotyczy)
  - Rodzaj reprezentacji (np. właściciel, wspólnik, członek zarządu)
  - Zakres uprawnień

### Przykładowy Request do API GUS/KRS
```http
GET /api/company-info?nip=1234567890 HTTP/1.1
Host: publicregistry.example.com
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
Content-Type: application/json
```

```
{
  "nip": "1234567890",
  "regon": "123456789",
  "name": "Przykładowa Firma Sp. z o.o.",
  "legal_form": "Spółka z o.o.",
  "status": "Aktywna",
  "registration_date": "2015-03-20",
  "addresses": {
    "headquarters": "ul. Przykładowa 10, 00-000 Warszawa",
    "correspondence": "ul. Inna 5, 00-000 Warszawa"
  },
  "owners": [
    {
      "name": "Jan Kowalski",
      "pesel": "80010112345",
      "role": "Prezes Zarządu",
      "representation": "Samodzielna"
    }
  ]
}

```

## Dane Uzupełniane przez Klienta
W przypadku niepełnych danych lub wymaganych dodatkowych informacji klient musi ręcznie wprowadzić następujące informacje:

### Dane finansowe:

Roczny przychód
Zysk netto
Wysokość zobowiązań finansowych
Wysokość kapitału zakładowego
Dokumenty finansowe:

### Sprawozdanie finansowe za ostatni rok
Rachunek zysków i strat
Bilans
Dane właścicieli / reprezentantów (jeśli nie zostały pobrane automatycznie lub wymagają aktualizacji):

Imię i nazwisko / Nazwa podmiotu
PESEL (jeśli dotyczy)
Adres zamieszkania
Numer i seria dowodu tożsamości
Walidacja Danych
System sprawdza poprawność uzupełnionych informacji, np.:

Spójność danych finansowych (np. porównanie zadeklarowanych przychodów ze sprawozdaniem finansowym)
Poprawność NIP i PESEL (zgodność ze wzorcem)
Aktualność danych w rejestrach publicznych
Interfejs użytkownika – Dynamic Forms
System umożliwia dynamiczne generowanie formularzy w oparciu o konfigurację danych, co ułatwia klientowi proces uzupełniania informacji.

## Przykładowy ekran wprowadzania danych:


Więcej o Dynamic Forms: https://agidot.eu/produkty/dynamic-forms/

Proces weryfikacji danych i powiadomienia
Automatyczna analiza danych: System pobiera i analizuje dane.
Uzupełnienie danych przez klienta: Klient podaje brakujące informacje.
Walidacja wprowadzonych danych: System sprawdza kompletność i poprawność wpisów.
Potwierdzenie i przejście do kolejnego etapu: Po pomyślnej walidacji klient jest przekierowywany do etapu weryfikacji tożsamości.
Powiadomienia:
Jeśli brakuje wymaganych informacji, klient otrzymuje powiadomienie e-mail / SMS z prośbą o ich uzupełnienie.
Po zakończeniu etapu system wysyła potwierdzenie o poprawnym uzupełnieniu danych.
