### 💼 Milestone D: Executive Business Presentation

I successfully built and audited a predictive machine learning pipeline to forecast package delivery times across our fullfillment network.
The model has verified statstically and regularized against overfitting, making it ready for automated production deployment.

1. What percentage of delivery variance does your model explain ($R^2$ value)?
Our model R^2 value is .998 which means our model successfully explained 99.8% of the total variation in our historical delivery times.
This shows an exceptionally high level of predictive stability.

2. Exactly how many hours longer or shorter do shipments from the **South_Hub** take compared to the baseline **East_Hub** (based on your categorical coefficient)?
With reference to East Hub, our model proves that shipments originating from the South Hub take an average of 4.46 hours LONGER keeping all other factor constant (under identical distance and traffice conditions)
This shows that the South Hub as a critical operational bottleneck that requires immediate process optimization.

3. Why did you drop the `Weather_Delay` column during your engineering audit?
We dropped the 'Weather_Delay' column because we detected severe multicollinearity. As it is mathematically tied to Distance_Miles, driving their Variance Inflation Factors close to 10.
Dropping it eliminated mathematical noise, allowing the OLS engine to calculated clean, stable and highly trustworthy coefficients for our remaining assets.

On average, when your machine learning model predicts how long a new package will take to deliver, its prediction is off by only  +-.8873 hours (approximately 53 minutes).
