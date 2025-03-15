## 1. Wstępna Rejestracja i Pozyskanie Podstawowych Danych [Klient]

**Opis:**  
Na tym etapie klient wprowadza podstawowe dane firmy, dane kontaktowe oraz akceptuje niezbędne zgody, które umożliwiają rozpoczęcie procesu pożyczkowego. Proces ten jest zintegrowany z systemem zgód (repozytorium zgód), który dynamicznie zwraca listę zgód startowych wymaganych dla procesu pożyczki online.

**Dane do wprowadzenia:**
- **Dane firmy:**
  - NIP – kluczowy identyfikator firmy, umożliwiający weryfikację w rejestrach publicznych.
- **Dane kontaktowe:**
  - Numer telefonu
  - Adres e-mail

**Integracja z Systemem Zgód:**  
System łączy się z repozytorium zgód, które zwraca listę zgód startowych dla procesu pożyczki online. Lista ta obejmuje zarówno zgody obowiązkowe, jak i zgody marketingowe.

**Lista Zgód Startowych:**
- **Podstawowe zgody:**
  - [ ] Akceptacja regulaminu i polityki prywatności.
  - [ ] Zgoda na przetwarzanie danych osobowych zgodnie z obowiązującymi przepisami (np. RODO).

- **Przykładowe zgody marketingowe:**
  - **Zgoda na kontakt telefoniczny:**  
    [ ] Wyrażam zgodę na kontakt telefoniczny w celu przedstawienia mi oferty produktów pożyczkowych firmy XYZ.
  - **Zgoda na wysyłkę wiadomości SMS:**  
    [ ] Wyrażam zgodę na otrzymywanie wiadomości SMS z informacjami o promocjach, ofertach specjalnych oraz nowościach produktów.
  - **Zgoda na otrzymywanie wiadomości e-mail:**  
    [ ] Wyrażam zgodę na otrzymywanie wiadomości e-mail zawierających informacje o produktach, aktualnościach oraz ofertach marketingowych.

**Uwagi:**  
Wszystkie zgody, pobierane przez integrację z repozytorium zgód, są dobrowolne (poza tymi obowiązkowymi) i mogą być w każdej chwili wycofane. Klient zostanie poinformowany o częstotliwości kontaktu oraz sposobie przetwarzania danych marketingowych.


### Przykładowy Request do Repozytorium Zgód

```http
GET /api/consents?process=loan_online HTTP/1.1
Host: consentrepo.example.com
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
Content-Type: application/json
```

Przykładowy Response z Repozytorium Zgód
```
{
  "process": "loan_online",
  "consents": [
    {
      "id": "terms",
      "label": "Akceptacja regulaminu i polityki prywatności",
      "required": true
    },
    {
      "id": "personal_data",
      "label": "Zgoda na przetwarzanie danych osobowych zgodnie z RODO",
      "required": true
    },
    {
      "id": "phone_contact",
      "label": "Wyrażam zgodę na kontakt telefoniczny w celu przedstawienia oferty produktów pożyczkowych",
      "required": false
    },
    {
      "id": "sms",
      "label": "Wyrażam zgodę na otrzymywanie wiadomości SMS z informacjami o promocjach, ofertach specjalnych oraz nowościach",
      "required": false
    },
    {
      "id": "email",
      "label": "Wyrażam zgodę na otrzymywanie wiadomości e-mail zawierających informacje o produktach, aktualnościach oraz ofertach marketingowych",
      "required": false
    }
  ]
}
```

## Widok przy pomocy dynamic-forms

### Struktura widoku w pliku Excel
![image](https://github.com/user-attachments/assets/3f9d8f4e-07cf-43cb-b745-c0016687741f)


### Widok 
![image](https://github.com/user-attachments/assets/8e8c7a79-79bb-4e2a-984c-199151afcd5a)

![image](https://github.com/user-attachments/assets/ead01e0f-093e-4e75-8379-4d3c3509de39)


Więcej o Dynamic Forms https://agidot.eu/produkty/dynamic-forms/
