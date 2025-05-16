გეთანხმები — აქ არის სუფთად და სწორად ფორმატირებული **ფოლდერის სტრუქტურა**, Markdown-ის წესებით, რომ სწორად გამოჩნდეს GitHub-ზე ან Markdown preview-ში:

```markdown
# საკრედიტო რისკის შეფასება ლოგისტიკური რეგრესიით

ამ პროექტის მიზანია ლოგისტიკური რეგრესიის გამოყენება საკრედიტო რისკის შეფასებისთვის.  
მოდელი პროგნოზირებს, დააბრუნებს თუ არა მომხმარებელი სესხს წარმატებით, ხელოვნურად შექმნილი `Risk` ცვლადის მიხედვით.

---

## 🔧 გამოყენებული ტექნოლოგიები

- Python  
- pandas  
- numpy  
- scikit-learn  
- matplotlib  
- seaborn  
- joblib  

---

## 📁 ფოლდერის სტრუქტურა

```

german-credit-risk-logistic-regression/
├── data/
│   ├── german\_credit\_data.csv
│   ├── X\_train.csv
│   ├── X\_test.csv
│   ├── y\_train.csv
│   ├── y\_test.csv
│   ├── logistic\_model.joblib
│   └── confusion\_matrix.png
├── src/
│   ├── preprocess.py
│   └── train\_model.py
├── requirements.txt
└── README.md

````

---

## 📥 1. მონაცემების წინასწარი დამუშავება

ფაილი: `src/preprocess.py`

- წაიკითხავს `german_credit_data.csv` ფაილს
- წაშლის `Unnamed: 0` სვეტს
- ხელოვნურად შექმნის `Risk` ცვლადს:
  - თუ არ აქვს "Saving accounts" ან "Checking account" ან `Credit amount > 5000` → `bad` (0)
  - სხვა შემთხვევაში → `good` (1)
- გარდაქმნის კატეგორიულ ცვლადებს One-Hot ფორმატში
- გაყოფს მონაცემებს 70/30-ზე და შეინახავს CSV ფაილებად

გაშვება:
```bash
python src/preprocess.py
````

---

## 🧠 2. მოდელის აგება და შეფასება

ფაილი: `src/train_model.py`

* სწავლობს ლოგისტიკურ მოდელს `LogisticRegression(max_iter=1000)`
* აფასებს შედეგებს Accuracy, Confusion Matrix, Classification Report
* ინახავს მოდელს `logistic_model.joblib` და მატრიცის გამოსახულებას `confusion_matrix.png`

გაშვება:

```bash
python src/train_model.py
```

---

## 📦 3. მოდელის ხელახალი გამოყენება

```python
import joblib
model = joblib.load("data/logistic_model.joblib")
predictions = model.predict(X_new)
```

---

## 📈 ვიზუალიზაცია

მოდელის დაბნეულობის მატრიცა ინახება ფაილად:

```
data/confusion_matrix.png
```

---

## ✅ ინსტალაცია

```bash
pip install -r requirements.txt
```

---

## 📚 წყარო

მონაცემები მიღებულია `German Credit Data` dataset-დან, ხოლო `Risk` ცვლადი დამატებულია პირობითი ლოგიკით მხოლოდ სასწავლო მიზნებისთვის.

```
```
