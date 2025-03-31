# 08-zatwierdzenie-decyzji-kredytowej.md


Po wygenerowaniu oferty kredytowej klient ma możliwość jej zaakceptowania lub odrzucenia. 

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
