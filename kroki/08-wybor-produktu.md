# 08-wybor-produktu.md

```
:WyborProduktu form
Wybór produktu pożyczkowego h3

ParametryPozyczki section
 Parametry pożyczki h5
 KwotaPozyczki textbox - Kwota pożyczki (PLN)
 OkresPozyczki textbox - Okres pożyczki (w miesiącach)
 TypPozyczki dropdown datasource="['personal','mortgage','consolidation']" - Typ pożyczki
 Dochod textbox - Miesięczny dochód (PLN)
 CreditScore textbox - Wynik kredytowy (np. 700)

WybranyProdukt section
 Wybrany produkt h5
 NazwaProduktu textbox - Nazwa produktu
 Oprocentowanie textbox - Oprocentowanie (%)
 RataMiesieczna textbox - Miesięczna rata (PLN)
 KwotaDoSplaty textbox - Całkowita kwota do spłaty (PLN)
 WarunkiProduktu datagrid
  Warunek column

Informacja textbox - Komunikat od systemu (np. informacja o powodzeniu wyboru produktu)

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

![image](https://github.com/user-attachments/assets/0f6d8983-f5c9-42c8-98e0-be231e0488d2)


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
