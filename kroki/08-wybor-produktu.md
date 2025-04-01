# 06-wybor-produktu.md

**Przykład API - Wybór produktu pożyczkowego:**
```
{
  "loan_amount": 10000,   // Kwota pożyczki
  "loan_term": 24,        // Okres pożyczki w miesiącach
  "loan_type": "personal", // Typ pożyczki (np. "personal", "mortgage", "consolidation")
  "income": 3500,          // Dochód w PLN
  "credit_score": 700      // Wynik kredytowy
}
```

```
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
```
