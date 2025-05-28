# 11-wyplata-srodkow.md

```
:PrzekazanieŚrodków form
Przekazanie środków h3

DanePrzelewu section
 Dane przelewu h5
 ID_pozyczki textbox - ID pożyczki
 ID_klient textbox - ID klienta
 Nr konta textbox - Numer konta bankowego (IBAN)

Podsumowanie section
 Podsumowanie operacji h5
 status label - Status operacji
 message label - Komunikat systemowy
 transaction_id label - ID transakcji
 transfer_date label - Data przelewu

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
![image](https://github.com/user-attachments/assets/1fcec705-53b6-4642-ba26-e1a111efb5fa)




**Przekazanie środków**

**Parametry żądania**
{
  "loan_id": "123456789",      // ID pożyczki
  "user_id": "987654321",      // ID klienta
  "bank_account": "PL61109010140000071219812874", // Numer konta klienta
  "amount": 10000,             // Kwota do przelania
  "transfer_method": "bank_transfer" // Metoda transferu (np. "bank_transfer", "cash")
}


**Odpowiedz:**

{
  "status": "success",
  "message": "Środki pożyczki zostały pomyślnie przelane na konto klienta.",
  "transaction_id": "abc123xyz456",
  "transfer_date": "2025-03-31"
}


Po zatwierdzeniu umowy i przeprowadzeniu weryfikacji system przekaże środki na konto klienta.
