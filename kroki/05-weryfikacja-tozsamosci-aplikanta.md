# 03-weryfikacja-tozsamosci-aplikanta.md
**Opis:**
Na tym etapie weryfikowana jest poprawność danych podana przez aplikanta
Weryfikacja tożsamości może obejmować różne metody, takie jak sprawdzenie numeru PESEL, numeru dowodu osobistego, zdjęć dokumentów tożsamości, czy nawet biometrie (np. rozpoznawanie twarzy).

Weryfikacja tożsamości w systemie
Inicjowanie weryfikacji: Na początku użytkownik podaje swoje dane osobowe (imię, nazwisko, PESEL, numer dokumentu tożsamości). Może być wymagane również potwierdzenie tożsamości za pomocą numeru telefonu lub e-maila (np. SMS lub e-mail z kodem weryfikacyjnym).

Przesyłanie dokumentów tożsamości: Następnie użytkownik przesyła zdjęcia swojego dokumentu tożsamości (np. dowodu osobistego) w formacie base64 lub innym, odpowiednim dla systemu.

Weryfikacja dokumentów: System analizuje przesłane zdjęcia dokumentów. Może to obejmować:

Sprawdzenie zgodności numeru dokumentu z bazą danych.

Wykrywanie oszustw związanych z fałszywymi dokumentami (np. analiza obrazu).

Weryfikacja, czy osoba na zdjęciu pasuje do zdjęcia w dokumencie (jeśli jest używana biometryczna weryfikacja twarzy).

Status weryfikacji: Po przeprowadzeniu analizy system informuje użytkownika, czy weryfikacja tożsamości zakończyła się sukcesem, czy nie. Jeśli weryfikacja się powiodła, użytkownik może kontynuować składanie wniosku o pożyczkę.

**Przykladowy request**
{
  "first_name": "Jan",
  "last_name": "Kowalski",
  "date_of_birth": "1985-07-15",
  "pesel": "85071512345",
  "identity_document_type": "dowód osobisty",
  "identity_document_number": "ABC1234567",
  "address": {
    "street": "ul. Przykładowa 10",
    "city": "Warszawa",
    "postal_code": "00-001",
    "country": "PL"
  },
  "phone_number": "+48 123 456 789",
  "email": "jan.kowalski@example.com"
}


**Przykładowy response**
{
  "status": "verification_started",
  "verification_id": "123456789",
  "message": "Weryfikacja tożsamości rozpoczęta pomyślnie. Proszę przesłać dokumenty tożsamości."
}



 Endpoint umożliwia użytkownikowi przesłanie dokumentów tożsamości (np. zdjęcia dowodu osobistego lub paszportu) w celu dalszej weryfikacji.

 **Przykladowy request**
 {
  "verification_id": "123456789",
  "identity_document_front_image": "base64_encoded_image_string",
  "identity_document_back_image": "base64_encoded_image_string"
}


**Przykładowy response**
{
  "status": "documents_received",
  "message": "Dokumenty tożsamości zostały przesłane. Przeprowadzamy weryfikację."
}


Endpoint pozwala sprawdzić status weryfikacji tożsamości użytkownika. Użytkownik może sprawdzić, czy jego tożsamość została pomyślnie zweryfikowana.

**Przykład zapytania**

GET /api/loan/application/identity-verification/status?verification_id=123456789


 **Przykladowy response**

 {
  "status": "verified",
  "message": "Weryfikacja tożsamości zakończona pomyślnie. Możesz kontynuować składanie wniosku o pożyczkę."
}

Lub

{
  "status": "failed",
  "message": "Weryfikacja tożsamości nie powiodła się. Proszę sprawdzić dane i spróbować ponownie."
}

 
