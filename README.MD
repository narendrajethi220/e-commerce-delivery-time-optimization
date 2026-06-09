## 🏬 The Scenario: E-Commerce Delivery Time Optimization

**The Business Problem:** You are consulting for a major logistics company. The Operations Director wants to predict **Delivery_Time** (in hours) for package shipments. They want to know which factors delay shipments and want an automated model to deploy to their cloud infrastructure.

They give you data with continuous variables, a categorical region variable, and a highly suspicious column that you need to statistically audit.

---

## 📊 Step 1: Copy-Paste the Dataset Generator

Run this Python code first to create your messy marketplace dataset of 1,200 shipments:

```python 
File is present inside the producer folder
```

---

## 🛠️ Your Capstone Tasks

### 🧩 Milestone A: Data Engineering & Architecture

1. **Vertical Split:** Separate your independent predictors (`X`) from your continuous response target (`y` = `Delivery_Time_Hrs`).
2. **One-Hot Encoding:** Convert `Warehouse_Region` into dummy variables. Use `drop_first=True` (or handle it so `East_Hub` becomes your missing **Reference Level**).
3. **Horizontal Split:** Split your data into **80% Training** and **20% Testing** sets using `sklearn`.

---

### 🔬 Milestone B: The Statistical Audit (`statsmodels`)

Before scaling or applying machine learning penalties, you must check the baseline mathematical health of your training data.

1. Explicitly add a constant column to your training features using `sm.add_constant()`.
2. Fit an `sm.OLS()` model and look at the summary report.
3. **Check Multicollinearity (VIF):** Calculate the VIF for your continuous columns (`Distance_Miles`, `Traffic_Delay_Hrs`, `Weather_Delay_Hrs`).
* *Hint: You will notice one VIF score is dangerously high because Weather Delay was mathematically tied to Distance.*


4. **The Cleanup Action:** Drop the column with the high VIF score from both your training and testing sets.
5. **Re-run the OLS model** with the cleaned feature list and review your new $p$-values. Are all remaining columns statistically significant ($p < 0.05$)?

---

### ⚙️ Milestone C: Production Pipeline (`scikit-learn`)

Now that your variables are clean and statistically verified, let's build the engineering code.

1. **Feature Scaling:** Separate your dummy variable columns from your continuous numerical columns. Apply `StandardScaler` **only** to the continuous columns on your training data, then transform the test data.
2. **Recombine:** Merge your scaled continuous columns back together with your unscaled binary dummy columns.
3. **Regularization:** Train an `sklearn.linear_model.Ridge(alpha=1.0)` model using this preprocessed training data.
4. **Generalization Test:** Predict delivery times for your untouched test set and calculate the **Mean Squared Error (MSE)**.

---

### 💼 Milestone D: Executive Business Presentation

Write down a simple 3-sentence summary message to send to the Operations Director via email, answering:

1. What percentage of delivery variance does your model explain ($R^2$ value)?
2. Exactly how many hours longer or shorter do shipments from the **South_Hub** take compared to the baseline **East_Hub** (based on your categorical coefficient)?
3. Why did you drop the `Weather_Delay` column during your engineering audit?

---

