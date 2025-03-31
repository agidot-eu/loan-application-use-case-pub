# 12-monitorowanie-splat-i-obsluga-posprzedazowa.md


Monitorowanie spłat pożyczki to proces, w którym zarówno pożyczkobiorca, jak i pożyczkodawca (np. bank) śledzą status płatności rat pożyczki. Bank lub instytucja finansowa monitoruje, czy klient realizuje spłaty na czas, a klient ma dostęp do informacji o stanie swoich zobowiązań, aby uniknąć opóźnień i naliczania dodatkowych kosztów. Systemy do monitorowania spłat pozwalają na automatyczne przypomnienia, raporty, oraz ułatwiają klientowi kontrolowanie swoich zobowiązań.

**1. Pobranie harmonogramu spłat**

**Parametry żądania:**

{
  "loan_id": "123456789",  // ID pożyczki
  "user_id": "987654321"   // ID klienta
}

**Odpowiedz:**
{
  "status": "success",
  "message": "Harmonogram spłat pożyczki został zwrócony.",
  "schedule": [
    {
      "payment_date": "2025-04-01",
      "amount_due": 500.00,
      "payment_status": "pending"
    },
    {
      "payment_date": "2025-05-01",
      "amount_due": 500.00,
      "payment_status": "pending"
    },
    {
      "payment_date": "2025-06-01",
      "amount_due": 500.00,
      "payment_status": "pending"
    }
  ]
}

**2. Powiadomienie o nadchodzącej racie**

**Parametry żądania:**
{
  "loan_id": "123456789",        // ID pożyczki
  "user_id": "987654321",        // ID klienta
  "payment_date": "2025-04-01",  // Data nadchodzącej raty
  "amount_due": 500.00,          // Kwota nadchodzącej raty
  "notification_type": "email",  // Typ powiadomienia (np. "email", "sms")
  "contact_info": "klient@example.com"  // Adres e-mail klienta
}

**Odpowiedz:**
{
  "status": "success",
  "message": "Powiadomienie o nadchodzącej racie zostało wysłane na adres e-mail klienta."
}

**3. Rejestracja płatności**

**Parametry żądania:**
{
  "loan_id": "123456789",        // ID pożyczki
  "user_id": "987654321",        // ID klienta
  "payment_date": "2025-03-31",  // Data wpłaty
  "amount_paid": 500.00,         // Kwota opłaconej raty
  "payment_method": "bank_transfer"  // Metoda płatności (np. "bank_transfer", "credit_card")
}

**Odpowiedz:**

{
  "status": "success",
  "message": "Płatność została zarejestrowana. Stan zadłużenia zaktualizowany.",
  "remaining_balance": 9500.00
}
