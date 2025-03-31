# 11-wyplata-srodkow.md

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
