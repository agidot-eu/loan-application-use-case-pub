# 10-zatwierdzenie-decyzji-kredytowej.md

Po wygenerowaniu oferty kredytowej klient ma możliwość jej zaakceptowania lub odrzucenia. 

```
:ZatwierdzenieDecyzjiKredytowej form
Zatwierdzenie decyzji kredytowej h3

DaneOferty section
 Identyfikatory oferty h5
 LoanId textbox - ID oferty kredytowej
 UserId textbox - ID klienta

AkceptacjaWarunkow section
 Akceptacja warunków h5
 AcceptedTerms checkbox - Akceptuję warunki pożyczki
 Signature textbox - Cyfrowy podpis (opcjonalny)

Informacja textbox - Status zatwierdzenia decyzji kredytowej

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

![image](https://github.com/user-attachments/assets/d3004fc1-e3c1-421a-aba2-bab80b89d4a4)


**Parametry akceptacji:**

{
  "loan_id": "123456789", // ID oferty kredytowej
  "user_id": "987654321", // ID klienta
  "accepted_terms": true, // Klient akceptuje warunki pożyczki
  "signature": "klient_signature" // Cyfrowy podpis klienta (opcjonalne)
}


**Odpowiedz:**

{
  "status": "success",
  "message": "Pożyczka została zatwierdzona. Środki zostaną przelane na wskazane konto bankowe."
}
