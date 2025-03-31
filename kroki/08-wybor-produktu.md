# 06-wybor-produktu.md

**Przykład API - Wybór produktu pożyczkowego:**
{
  "loan_amount": 10000,   // Kwota pożyczki
  "loan_term": 24,        // Okres pożyczki w miesiącach
  "loan_type": "personal", // Typ pożyczki (np. "personal", "mortgage", "consolidation")
  "income": 3500,          // Dochód w PLN
  "credit_score": 700      // Wynik kredytowy
}


{
  "status": "success",
  "selected_product": {
    "product_name": "Pożyczka gotówkowa standard",
    "loan_amount": 10000,
    "interest_rate": 8.5,  // Oprocentowanie pożyczki
    "monthly_payment": 500, // Miesięczna rata
    "total_amount_to_repay": 12000,  // Całkowita kwota do spłaty
    "loan_type": "personal",
    "terms": [
      "Bez ukrytych opłat",
      "Okres spłaty do 36 miesięcy",
      "Decyzja kredytowa online"
    ]
  },
  "message": "Wybór produktu pożyczkowego zakończony sukcesem. Możesz przejść do składania wniosku."
}


Opis:
loan_amount: Kwota, którą użytkownik chce pożyczyć.

loan_term: Okres spłaty pożyczki (w miesiącach).

loan_type: Typ pożyczki, np. gotówkowa, hipoteczna, konsolidacyjna.

income: Dochód osoby ubiegającej się o pożyczkę (potrzebne do oceny zdolności kredytowej).

credit_score: Wynik kredytowy, który jest istotny w ocenie ryzyka.

W odpowiedzi API, użytkownik otrzymuje informacje o wybranym produkcie pożyczkowym, jak oprocentowanie, rata miesięczna, całkowita kwota do spłaty oraz warunki oferty.


**Kolejny krok:**

Po wybraniu produktu użytkownik może przejść do składania pełnego wniosku:

{
  "personal_data": {
    "full_name": "Jan Kowalski",
    "address": "ul. Przykładowa 1, Warszawa",
    "email": "jan.kowalski@example.com",
    "phone": "+48123456789"
  },
  "employment_info": {
    "company_name": "XYZ Ltd.",
    "position": "Programista",
    "monthly_income": 3500
  },
  "loan_details": {
    "loan_amount": 10000,
    "loan_term": 24,
    "loan_type": "personal"
  },
  "bank_account": {
    "bank_name": "Bank XYZ",
    "account_number": "1234567890"
  }
}


Taki wniosek uruchamia proces kredytowy, po którym użytkownik otrzymuje decyzję o przyznaniu pożyczki lub o konieczności dostarczenia dodatkowych informacji.
