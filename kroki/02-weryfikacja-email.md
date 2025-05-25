## **2. Weryfikacja SMS [Klient]**  
- **Opis:**  
  Po podaniu numeru telefonu klient otrzymuje wiadomość SMS z 4-cyfrowym kodem, który musi wprowadzić w systemie, aby przejść dalej.  

```
:WeryfikacjaEmail form
Weryfikacja adresu e-mail h3

SekcjaKod section
 Wprowadź kod otrzymany na e-mail h5
 Kod textbox mask="999999" - Kod weryfikacyjny (6 cyfr)

AkcjaZweryfikuj button action="VerifyCode" - Zweryfikuj kod
```
![image](https://github.com/user-attachments/assets/ca8ac36c-42b5-45a7-a738-ef8ad217e874)
