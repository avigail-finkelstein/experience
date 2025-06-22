##  מדריך התקנה והרצה לסביבות

###  סביבות עבודה:
- `dev` – פיתוח  
- `test` – בדיקות  
- `prod` – ייצור

###  התקנה מקומית:
```bash
git clone ...
cd project-name
cp .env.dev .env
npm install
npm run dev
```

---

##  CI/CD – תהליך אוטומטי

| סביבה | טריגר | פעולות |
|-------|--------|---------|
| dev   | push ל־`dev`   | בדיקות + build |
| test  | push ל־`test`  | בדיקות + deploy לבדיקה |
| prod  | merge ל־`main` | בדיקות + deploy לייצור |

---

##  קונפיגורציה

- קובצי סביבה:  
  `.env.dev`, `.env.test`, `.env.prod`

- סיסמאות ו־API Keys מנוהלים דרך GitHub Secrets:  
  `Settings → Secrets → Actions`

---

##  הרצת בדיקות

```bash
npm run test              # בדיקות יחידה
npm run test:integration  # בדיקות אינטגרציה
```

---

##  עדכון התהליך

- קבצי Workflow נמצאים בתיקייה `.github/workflows`
- לכל סביבה יש קובץ משלה (`dev.yml`, `test.yml`, `prod.yml`)
- כל שינוי ב־Workflow עובר אוטומציה בהתאם ל־branch
