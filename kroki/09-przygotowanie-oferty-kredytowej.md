# 07-przygotowanie-oferty-kredytowej.md

Przygotowanie oferty kredytowej przez bank w odpowiedzi na wniosek o pożyczkę zwykle odbywa się po tym, jak bank zbierze wszystkie niezbędne informacje o kliencie (np. dochody, historię kredytową) i dokona analizy zdolności kredytowej. Następnie generuje ofertę, która zawiera szczegóły pożyczki (wysokość kwoty, oprocentowanie, okres spłaty, miesięczna rata itp.).

{
  "loan_amount": 10000,   // Kwota pożyczki
  
  "loan_term": 24,        // Okres pożyczki w miesiącach
  
  "loan_type": "personal", // Typ pożyczki (np. "personal", "mortgage")
  
  "income": 3500,          // Dochód miesięczny klienta
  
  "credit_score": 700,     // Wynik kredytowy klienta
  
  "employment_status": "full_time", // Status zatrudnienia
  
  "existing_loans": [     // Lista istniejących pożyczek
    {
      "loan_type": "car_loan",
      "remaining_balance": 5000,
      "monthly_payment": 300
    }
  ]
}



**Opis parametrów:**

loan_amount: Kwota pożyczki, którą klient chce uzyskać.

loan_term: Okres spłaty pożyczki w miesiącach.

loan_type: Typ pożyczki, np. gotówkowa, hipoteczna.

income: Miesięczny dochód klienta, istotny przy ocenie zdolności kredytowej.

credit_score: Wynik kredytowy, wpływa na ofertowane warunki pożyczki.

employment_status: Status zatrudnienia klienta, np. pełny etat, samozatrudniony.

existing_loans: Istniejące pożyczki klienta, jeśli są (informacje o saldach i ratach).



**Przykładowa odpowiedź:**

{
  "status": "success",
  "offer": {
    "product_name": "Pożyczka gotówkowa",
    "loan_amount": 10000,
    "interest_rate": 8.5,   // Oprocentowanie roczne
    "loan_term": 24,        // Okres pożyczki
    "monthly_payment": 500, // Miesięczna rata
    "total_amount_to_repay": 12000,  // Całkowita kwota do spłaty
    "available_balance": 10000, // Dostępna kwota pożyczki
    "repayment_schedule": [
      {
        "month": 1,
        "payment": 500
      },
      {
        "month": 2,
        "payment": 500
      },
      // i tak dalej, dla każdego miesiąca
    ],
    "terms": [
      "Oprocentowanie stałe 8.5% rocznie",
      "Brak dodatkowych ukrytych opłat",
      "Decyzja kredytowa online",
      "Możliwość wcześniejszej spłaty bez dodatkowych kosztów"
    ]
  },
  "message": "Oferta kredytowa została przygotowana. Możesz zaakceptować warunki lub skontaktować się z bankiem."
}


**Opis odpowiedzi:**

product_name: Nazwa produktu pożyczkowego (np. pożyczka gotówkowa).

loan_amount: Kwota, którą klient może pożyczyć.

interest_rate: Oprocentowanie roczne pożyczki.

loan_term: Okres, przez który klient będzie spłacał pożyczkę.

monthly_payment: Miesięczna rata, którą klient będzie płacił przez cały okres kredytowania.

total_amount_to_repay: Całkowita kwota, jaką klient będzie musiał spłacić (kwota pożyczki + odsetki).

repayment_schedule: Szczegółowy harmonogram spłat, pokazujący miesięczne raty do zapłaty.

terms: Warunki pożyczki (np. oprocentowanie, opłaty dodatkowe, możliwość wcześniejszej spłaty).
