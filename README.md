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
│   ├── german\_credit\_data.csv         # საწყისი მონაცემები
│   ├── X\_train.csv / X\_test.csv       # გაწმენდილი მონაცემები
│   ├── y\_train.csv / y\_test.csv       # მიზნობრივი ცვლადები
│   ├── logistic\_model.joblib          # შენახული მოდელი
│   └── confusion\_matrix.png           # მოდელის ვიზუალიზაცია
│
├── src/
│   ├── preprocess.py                  # მონაცემების გაწმენდა და გადამუშავება
│   └── train\_model.py                 # მოდელის სწავლა, შეფასება და შენახვა
│
├── requirements.txt
└── README.md

````

---

## 📥 1. მონაცემების წინასწარი დამუშავება

**ფაილი:** `src/preprocess.py`

- წაიკითხავს `german_credit_data.csv` ფაილს
- წაშლის `Unnamed: 0` სვეტს
- ხელოვნურად შექმნის `Risk` ცვლადს შემდეგი ლოგიკით:
  - თუ არ აქვს „Saving accounts“ ან „Checking account“ **ან** `Credit amount > 5000` → `bad` (0)
  - სხვა შემთხვევაში → `good` (1)
- კატეგორიულ ცვლადებს გარდაქმნის One-Hot ფორმატში
- დაყოფს მონაცემებს 70/30-ზე და შეინახავს 4 ცალკე CSV ფაილად

**გაშვება:**
```bash
python src/preprocess.py
````

---

## 🧠 2. ლოგისტიკური რეგრესიის მოდელის აგება

**ფაილი:** `src/train_model.py`

* ჩატვირთავს გაწმენდილ მონაცემებს CSV-ებიდან
* ააგებს ლოგისტიკურ მოდელს `LogisticRegression(max_iter=1000)`
* შეაფასებს:

  * `accuracy`
  * `confusion matrix`
  * `classification report`
* შეინახავს:

  * მოდელს: `data/logistic_model.joblib`
  * ვიზუალიზაციას: `data/confusion_matrix.png`

**გაშვება:**

```bash
python src/train_model.py
```

---

## 📦 3. შენახული მოდელის გამოყენება

შეიძლება ხელახლა გამოიყენო მოდელი სხვა პროექტში ასე:

```python
import joblib
model = joblib.load("data/logistic_model.joblib")
predictions = model.predict(X_new)
```

---

## 📈 ვიზუალიზაცია

მოდელის დაბნეულობის მატრიცა (Confusion Matrix) შეინახება ფაილად:

```
data/confusion_matrix.png
```

რომლის ნახვაც შესაძლებელი იქნება როგორც სურათი.

---

## ✅ ინსტალაცია

საჭირო ბიბლიოთეკები ჩამოწერილია `requirements.txt` ფაილში.

დაყენება:

```bash
pip install -r requirements.txt
```

---

## 📚 წყარო

მონაცემები მიღებულია Kaggle-ზე დაფუძნებული `German Credit Data` dataset-იდან.
`Risk` ცვლადი დამატებულია მხოლოდ სასწავლო მიზნებისთვის, იმიტირებული ლოგიკით.

```
