# 09-przygotowanie-oferty-kredytowej.md
```
:PrzygotowanieOfertyKredytowej form
Przygotowanie oferty kredytowej h3

DaneKlienta section
 Dane klienta h5
 KwotaPozyczki textbox - Kwota pożyczki (PLN)
 OkresPozyczki textbox - Okres spłaty (w miesiącach)
 TypPozyczki dropdown datasource="['personal','mortgage']" - Typ pożyczki
 Dochod textbox - Miesięczny dochód (PLN)
 CreditScore textbox - Wynik kredytowy
 StatusZatrudnienia dropdown datasource="['full_time','self_employed','part_time','unemployed']" - Status zatrudnienia

IstniejacePozyczki datagrid
 Istniejące pożyczki klienta h5
 TypPozyczki column
 SaldoPozostale column
 RataMiesieczna column

OfertaKredytowa section
 Oferta kredytowa h5
 NazwaProduktu textbox - Nazwa produktu
 KwotaPrzyznana textbox - Kwota przyznana (PLN)
 Oprocentowanie textbox - Oprocentowanie (% rocznie)
 Okres textbox - Okres pożyczki (miesiące)
 RataMiesieczna textbox - Miesięczna rata (PLN)
 KwotaLacznaDoSplaty textbox - Całkowita kwota do spłaty (PLN)
 DostepnaKwota textbox - Dostępna kwota (PLN)

HarmonogramSplaty datagrid
 Harmonogram spłat
 Miesiac column
 KwotaRaty column

WarunkiOferty datagrid
 Warunki oferty
 Warunek column

Informacja textbox - Komunikat systemowy (np. "Oferta kredytowa została przygotowana...")

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

![image](https://github.com/user-attachments/assets/cfc4beda-0f72-478f-baf1-5db820da3bcb)


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
