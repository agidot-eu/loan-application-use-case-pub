# 06-weryfikacja-tozsamosci-reprezentantow.md

Szczegóły procesu weryfikacji reprezentanta
Inicjowanie weryfikacji: Na początku użytkownik (reprezentant) składa dane osobowe (imię, nazwisko, numer dokumentu tożsamości) oraz dane organizacji, którą reprezentuje. Do tych danych dołączane są informacje o firmie, takie jak numer REGON, NIP, pełnomocnictwo, a także stanowisko reprezentanta.

Przesyłanie dokumentów: W kolejnej fazie reprezentant musi przesłać dokumenty, które potwierdzają jego uprawnienia do reprezentowania organizacji. Może to być pełnomocnictwo, umowa o pracę, dokumenty rejestrowe firmy (np. KRS, NIP), dokumenty potwierdzające jego rolę w firmie.

Weryfikacja dokumentów: Po otrzymaniu dokumentów system przetwarza je, sprawdzając:

Czy dokumenty potwierdzają uprawnienia reprezentanta.

Czy dane w dokumentach są spójne z danymi firmy (np. sprawdzenie numeru NIP/REGON firmy).

Weryfikacja tożsamości reprezentanta na podstawie przesłanych dokumentów.

Status weryfikacji: Po przeprowadzeniu weryfikacji system generuje status, który informuje, czy reprezentant został pomyślnie zweryfikowany. Jeśli weryfikacja zakończy się sukcesem, reprezentant może kontynuować składanie wniosku o pożyczkę w imieniu firmy.


```
:WeryfikacjaReprezentanta form
Weryfikacja tożsamości reprezentanta h3

DaneReprezentanta section
 Dane osobowe reprezentanta h5
 Imie textbox - Imię reprezentanta
 Nazwisko textbox - Nazwisko reprezentanta
 NumerDokumentu textbox - Numer dokumentu tożsamości
 Stanowisko textbox - Stanowisko w firmie

DaneFirmy section
 Dane organizacji h5
 NazwaFirmy textbox - Pełna nazwa firmy
 Nip textbox - Numer NIP firmy
 Regon textbox - Numer REGON firmy

DokumentyReprezentanta section
 Dokumenty potwierdzające uprawnienia h5
 DokumentPelnomocnictwa textbox - Pełnomocnictwo (base64 lub inny format)
 DokumentUmowyPracy textbox - Umowa o pracę (jeśli dotyczy)
 DokumentKRS textbox - Dokument rejestrowy (KRS)
 DokumentNIP textbox - Dokument NIP firmy
 InneDokumenty textbox - Inne dokumenty potwierdzające rolę

WeryfikacjaSystemowa section
 Weryfikacja systemowa h5
 CzyDaneZgodne checkbox - Potwierdzam zgodność danych z dokumentami firmy
 CzyUprawnieniaSprawdzone checkbox - Potwierdzam, że dokumenty potwierdzają moje uprawnienia reprezentacyjne

StatusWeryfikacji section
 Status weryfikacji h5
 Status dropdown datasource="['Oczekuje','Zatwierdzono','Odrzucono']" - Aktualny status procesu weryfikacji
 Komentarz textbox - Komentarz do weryfikacji (np. powód odrzucenia)

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

![image](https://github.com/user-attachments/assets/1d4f36d6-b4af-4668-9d15-be0f9195efc2)
