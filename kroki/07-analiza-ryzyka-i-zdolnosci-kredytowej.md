# 07-analiza-ryzyka-i-zdolnosci-kredytowej.md

Kluczowe funkcje:
Obliczanie wskaźnika DTI – stosunek długów do dochodów.

Ocena ryzyka – prosta klasyfikacja na podstawie DTI i zdolności do spłaty.

```
:AnalizaRyzykaIKredytowej form
Analiza ryzyka i zdolności kredytowej h3

DaneFinansowe section
 MiesiecznyDochód textbox - Miesięczny dochód netto (PLN)
 MiesieczneZobowiazania textbox - Miesięczne zobowiązania (PLN)

WskaznikiFinansowe section
 DTI textbox - Wskaźnik DTI (Debt-To-Income, w %) - obliczany jako (zobowiązania / dochód) * 100
 CzyDTIOk checkbox - DTI w akceptowalnym zakresie

OcenaRyzyka section
 Ocena dropdown datasource="['niskie','średnie','wysokie']" - Klasyfikacja poziomu ryzyka na podstawie danych
 KomentarzAnalizy textbox - Komentarz analityka

DecyzjaKredytowa section
 StatusDecyzji dropdown datasource="['zatwierdzony','odrzucony','wymaga analizy']" - Status decyzji kredytowej
 Uzasadnienie textbox - Uzasadnienie decyzji lub dalszych kroków

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
![image](https://github.com/user-attachments/assets/5c41ccd4-3d65-41b2-a7cf-481c471744bb)


Decyzja kredytowa – API zwraca status: "zatwierdzony", "odrzucony" lub "wymaga analizy".


**Przykładowe żądanie POST**
```
{
    "income": 5000,
    "expenses": 1500,
    "credit_score": 720,
    "loan_amount": 20000
}
```

**Przykładowa odpowiedź API**
```
{
    "dti": 0.3,
    "credit_score": 720,
    "loan_amount": 20000,
    "decision": "Zatwierdzony"
}
```

**Kod API**

```
from flask import Flask, request, jsonify

app = Flask(__name__)

def calculate_dti(income, expenses):
    """Oblicza wskaźnik DTI (Debt-to-Income)"""
    if income == 0:
        return 1  # Maksymalne ryzyko, brak dochodów
    return round(expenses / income, 2)

def assess_credit_risk(dti, credit_score, loan_amount, income):
    """Ocena zdolności kredytowej na podstawie DTI i scoringu"""
    if dti > 0.5 or credit_score < 500:
        return "Odrzucony"
    elif dti < 0.35 and credit_score > 700 and loan_amount < income * 5:
        return "Zatwierdzony"
    return "Wymaga analizy"

@app.route('/analyze_credit', methods=['POST'])
def analyze_credit():
    data = request.json
    income = data.get("income")
    expenses = data.get("expenses")
    credit_score = data.get("credit_score")
    loan_amount = data.get("loan_amount")

    if None in [income, expenses, credit_score, loan_amount]:
        return jsonify({"error": "Brak wymaganych danych"}), 400

    dti = calculate_dti(income, expenses)
    decision = assess_credit_risk(dti, credit_score, loan_amount, income)

    return jsonify({
        "dti": dti,
        "credit_score": credit_score,
        "loan_amount": loan_amount,
        "decision": decision
    })

if __name__ == '__main__':
    app.run(debug=True)

```
