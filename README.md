# פרויקט חיזוי דירוג סרטים - למידת מכונה (חלק 2)

**מגישות:** מרים דינאי | הילה הלברשטט

## תיאור הפרויקט
פרויקט זה בונה מודל למידת מכונה החוזה את הדירוג הממוצע של סרטים (averageRating) טרם יציאתם לאקרנים, בהתבסס על נתוני IMDb. המודל שנבחר והציג את הביצועים הטובים ביותר הוא **Random Forest**.

## קבצים מצורפים
* `notebook.ipynb`: מחברת הקוד המלאה הכוללת את עיבוד הנתונים, הנדסת הפיצ'רים, אימון המודלים והניתוחים (Fairness & Error Analysis).
* `model.pkl`: המודל המאומן הסופי (Random Forest בתוך Pipeline).
* `prepare_data`: פונקציה מובנית בתוך המחברת המקבלת DataFrame גולמי ומחזירה DataFrame מעובד.
* `report.pdf`: דוח הפרויקט המפרט את תהליך העבודה, המסקנות וניתוח השגיאות.
* `requirements.txt`: רשימת ספריות הפייתון הנדרשות להרצת הקוד.

## הוראות הרצה (Test Time)
כדי לייצר תחזיות על סט נתונים חדש במעמד ההגנה, יש להריץ את הרצף הבא בסביבת הפייתון:

1. התקנת הספריות: `pip install -r requirements.txt`
2. ייבוא הספריות, קריאת הנתונים וטעינת המודל:

```python
import pandas as pd
import joblib
from notebook import prepare_data # Assuming prepare_data is accessible

# 1. קריאת קובץ הבדיקה
df_2025 = pd.read_csv('test_dataset.csv')

# 2. עיבוד הנתונים
X_test = prepare_data(df_2025)

# 3. טעינת המודל
model = joblib.load('model.pkl')

# 4. יצירת תחזיות
y_pred = model.predict(X_test)
