# nmolya
import pandas as pd
from catboost import CatBoostRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, r2_score

data = pd.read_csv('C:/Users/MOLYA/Desktop/salarykz.csv')
data['Score'] = data['Score'].str.replace(',', '').astype(float)
X = data[['Rank', 'SubmissionCount']]
y = data['Score']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
model = CatBoostRegressor()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
print(f'Mean Squared Error: {mse}')
print(f'R-squared (R2): {r2}')
